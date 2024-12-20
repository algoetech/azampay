
# Azampay PHP Integration Package

A robust PHP package for seamless integration with Azampay payment services, supporting Mobile Money (MNO), Bank, and Merchant payment options.

## Features

- Mobile Money (MNO) payments integration
- Bank payments processing
- Merchant services support
- Environment switching (Sandbox/Production)
- Simple credential management
- Flexible service selection

## Installation

```bash
composer require taitech/azampay
```

## Quick Start

```php
use Taitech\Azampay\AzampayService;

// Initialize the service
$azampay = new AzampayService(
    appName: 'YOUR_APP_NAME',
    clientId: 'YOUR_CLIENT_ID',
    secret: 'YOUR_CLIENT_SECRET',
    env: 'SANDBOX', // or 'PRODUCTION'
    service: 'MNO' // or 'BANK' or 'MERCHANT'
);
```


## Configuration
The package requires the following configuration parameters:

- appName: Your application name registered with Azampay
- clientId: Your Azampay client ID
- secret: Your Azampay client secret
- env: Environment setting (SANDBOX or PRODUCTION)
- service: Service type (MNO, BANK, or MERCHANT)
- 
## Service Types
### Mobile Money (MNO)
```php
$azampay = new AzampayService(
    appName: 'YOUR_APP_NAME',
    clientId: 'YOUR_CLIENT_ID',
    secret: 'YOUR_CLIENT_SECRET',
    env: 'SANDBOX', // or 'PRODUCTION'
    service: 'MNO'
);
```
### Bank Payments
```php
$azampay = new AzampayService(
    appName: 'YOUR_APP_NAME',
    clientId: 'YOUR_CLIENT_ID',
    secret: 'YOUR_CLIENT_SECRET',
    env: 'SANDBOX', // or 'PRODUCTION'
    service: 'BANK'
);
```
### Merchant Services
```php
$azampay = new AzampayService(
    appName: 'YOUR_APP_NAME',
    clientId: 'YOUR_CLIENT_ID',
    secret: 'YOUR_CLIENT_SECRET',
    env: 'SANDBOX', // or 'PRODUCTION'
    service: 'MERCHANT'
);
```

## Usage
### Initiate Payment and Checkout
```php
// vendor credentials
$app = 'YOUR_APP_NAME';
$clientId = 'YOUR_CLIENT_ID';
$secret = 'YOUR_SECRET_KEY';


try {
     $azampay = new AzampayService(
        $app, // App Name
        $clientId, // Client ID
        $secret, // Client Secret
        'SANDBOX', // Environment (SANDBOX/PRODUCTION)
        'MNO', // Service (MNO, BANK, MERCHANT)
    );

    // Example of calling the checkout method for MNO [MOBILE PAYMENT]
    $payload = [
        'amount' => 5000,
        'accountNumber' => '255713295803',
        'provider' => 'Tigo',
        'additionalProperties' => [
                'router' => "Home",
                'mac' => "A6:47:F6:52:38:D5",
            ],
    ];

    $response = $azampay->checkout($payload);

    // Output the final JSON response
    header('Content-Type: application/json');
    echo json_encode($response, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);

} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
}
```



## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Create a new Pull Request
6. Ensure your code adheres to the project's coding standards
7. Provide clear and concise commit messages

For more details, please refer to the [CONTRIBUTING](CONTRIBUTING.md) file.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support
For any issues or questions, please open an issue on the GitHub repository.

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2024-01-01

### Added
- Initial release
- Support for Mobile Money (MNO) payments
- Support for Bank payments
- Support for Merchant services
- Environment switching capability
- Flexible service selection



