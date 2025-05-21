# WikiAphpi

> [!NOTE]
> This project only exists because the author is very lazy and not very prone to learn a entire new library and rewrite everything just to do some simple tasks. It may not be the best solution for your needs, but it works for the author. The documentation is not very good, but it is better than nothing. If you want to improve it, please do so.

WikiAphpi is a PHP library designed to interact with the MediaWiki API. It provides a set of classes and traits to perform various actions such as reading, editing, deleting, and uploading content to a MediaWiki instance. The library supports multiple authentication methods, including OAuth and mock testing.

## Features

- **Unlogged Requests**: Perform API requests without authentication.
- **Logged Requests**: Authenticate with a username and password to perform API actions.
- **OAuth Authentication**: Use OAuth for secure API interactions.
- **Mock Testing**: Simulate API interactions for testing purposes.
- **Content Retrieval**: Fetch page content, sections, and check page existence.
- **Content Modification**: Edit, delete, move pages, and upload files.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/albertoleoncio/WikiAphpi.git
   ```
2. Include the library in your project:
   ```php
   require_once 'path/to/WikiAphpi/main.php';
   ```

## Usage

### Basic Example

```php
require_once 'path/to/WikiAphpi/main.php';

// Example for unlogged requests
$api = new WikiAphpiUnlogged('https://example.com/api.php');
$response = $api->performRequest(['action' => 'query', 'format' => 'json'], false);
print_r($response);
```

### Logged Example

```php
require_once 'path/to/WikiAphpi/main.php';

$api = new WikiAphpiLogged('https://example.com/api.php', 'username', 'password');
$response = $api->performRequest(['action' => 'query', 'format' => 'json'], false);
print_r($response);
```

### OAuth Example

```php
require_once 'path/to/WikiAphpi/main.php';

$api = new WikiAphpiOAuth('https://example.com/api.php', 'consumerKey', 'consumerSecret');
$api->setup();
$response = $api->performRequest(['action' => 'query', 'format' => 'json'], false);
print_r($response);
```

### Mock Example

```php
require_once 'path/to/WikiAphpi/main.php';

$api = new WikiAphpiTest('https://example.com/api.php', 'username', 'password');
$response = $api->edit('Sample content', null, true, 'Edit summary', 'Sample Page');
print_r($response);
```

## Classes and Traits

### Classes

- `WikiAphpiUnlogged`: For unlogged API requests.
- `WikiAphpiLogged`: For logged API requests using username and password.
- `WikiAphpiOAuth`: For API requests using OAuth authentication.
- `WikiAphpiTest`: For mocking API requests during testing.

### Traits

- `WikiAphpiSee`: Provides methods for content retrieval.
- `WikiAphpiDo`: Provides methods for content modification.
- `WikiAphpiBehalf`: Provides methods for OAuth-based actions.
- `WikiAphpiMock`: Provides methods for mocking API actions.

## Exception Handling

The library includes a custom exception class `ContentRetrievalException` to handle errors during API interactions.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact

For questions or support, please open an issue on the GitHub repository.
