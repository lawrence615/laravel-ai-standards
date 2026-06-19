# Laravel Development Standards

## Architecture
- Use Repository Pattern.
- Every repository must have an interface.
- Implementations are stored in `app/Repositories/`, with interface in `app/Interfaces/`

## Dependency Injection
- Use constructor injection for dependencies.
- Avoid using `app()` helper for resolving dependencies.
- Use `app()->make()` only in exceptional cases.
- Register bindings in service providers.

Example:

```php
public function __construct(
    private readonly ClientKycRepositoryInterface $clientKycRepository
) {}
```

## Repository Binding
All bindings must be registered in `app/Providers/RepositoryServiceProvider.php` in the `register()` method.

Example:

```php
$this->app->bind(ClientKycRepositoryInterface::class, ClientKycRepository::class);
```

## DTOs
Use DTOs whenever:
- Posting to external APIs
- Passing structured data between layers
- Complex request transformations

### Location
app/DTOs/

## Validation
Use Form Requests.

Never validate inside controllers.

## Responses
All API response logic must be centralized in a Response class.

### Location
app/Responses/

### Rule
- Never return raw JSON responses directly from controllers, jobs, or services.
- All responses must go through a dedicated Response class.
- Controllers should only call response helpers.
- Controllers must NEVER:
  - return response()->json()
  - format API responses manually
  - handle DB rollbacks

### Base Response Class Example
```
<?php

namespace App\Classes;

use Illuminate\Support\Facades\DB;
use Illuminate\Http\Exceptions\HttpResponseException;

class ApiResponse
{
    public static function rollback($e, $message = "Something went wrong! Process not completed.")
    {
        DB::rollBack();
        self::throw($e, $message);
    }

    public static function throw($e, $message = "Something went wrong! Process not completed", $code = 500)
    {
        // Log::error('ApiResponse', ['error'=> $e->getMessage()]);
        throw new HttpResponseException(response()->json(["message" => $message], $code));
    }

    public static function sendResponse($result, $message, $code = 200)
    {
        $response = [
            'success' => true,
            'data'    => $result
        ];
        if (!empty($message)) {
            $response['message'] = $message;
        }
        return response()->json($response, $code);
    }
}
```

## Traits
Use Traits only for reusable cross-cutting concerns.

Examples:
- Phone normalization
- Audit logging
- Common hel

### Location
app/Traits/

## Controllers
Controllers should only handle HTTP requests and responses.
They should delegate business logic to services. Controllers should remain thin.

