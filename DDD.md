# Structure
```
-bin
-config
-public
-src
    -Application
    -Controller
    -Domain
        -League
            League.php
        -Player
            Player.php
        -Team
            Team.php
    -Infrastructure
    -Repository
```

Game.php
```php
namespace Guess\Domain\Game;

use Guess\Domain\Team\Team;

class Game
{
    private int $id;
    private string $score;
    private Team $homeTeam;
    //...
}
```

# [Dependance inversion](https://fmo.medium.com/dependency-inversion-principle-in-a-hexagonal-architecture-3291ea4d5202)

# Security and JWT
```sh
composer require "lexik/jwt-authentication-bundle"
```

```php
//Player.php
use Symfony\Component\Security\Core\User\UserInterface;
class Player implements UserInterface
{
    //... impement getRoles() getSalt() eraseCredentials
}
```

## config security.yaml
algorithm, property, check_path, register...

## Generate the SSL keys:
```sh
mkdir -p config/jwt
openssl genkey -out config/jwt/private.pem -aes256 -algorithm rsa -pkeyopt rsa_keygen_bits:4096
openssl pkey -in config/jwt/private.pem -out config/jwt/public.pem -pubout
```
## .env:
```
JWT_PASSPHRASE=password
```
## Change Namespace to Our App
- Service.yaml
- Kernel.php
- Composer.json - composer dump-autoload
- Index.php
- DataFixtures

### 