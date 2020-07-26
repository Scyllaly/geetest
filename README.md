# Geetest 极验

## Install

``` bash
composer require scyllaly/geetest
```

## config

- insert ServiceProvider into `config/app.php`
	
```php
Scyllaly\Geetest\GeetestServiceProvider::class,
```

- insert Alias into `config/app.php` 

 ```php
 'Geetest' => Scyllaly\Geetest\Geetest::class,
 ```

- publish config & view file

```shell
php artisan vendor:publish --provider='Scyllaly\Geetest\GeetestServiceProvider'
```

- insert config fileds into `.env` , or get the config by `CaptchaVerify` Component
 ```
GEETEST_ID=
GEETEST_KEY=
```

## View Config Fields

| 配置项  | 说明  | 选项  | 默认值  |
| ------------: | :------------ | :------------ | :------------ |
| width | 按钮宽度  | 单位可以是 px, %, em, rem, pt  | 300px|
| lang | 语言，极验验证码免费版不支持多国语言  | zh-cn, en, zh-tw, ja, ko, th  | zh-cn  |
| server-get-config | 从服务器获取GeetestKEY | True | False          |
| product  | 验证码展示方式  | popup, float  | popup  |
| geetest_id  | 极验验证码ID  |   |   |
| geetest_key  | 极验验证码KEY  |   |   |
| client_fail_alert  | 客户端失败提示语  |   | 请完成验证码  |
| server_fail_alert  | 服务端失败提示语  |   | 验证码校验失败  |

## Usage

- render your web page

```php
{!! Geetest::render() !!}
```

- request Validate

```php
$this->validate($request, [
    'geetest_challenge' => 'required|geetest'
], [
    'geetest' => config('geetest.server_fail_alert')
]);
```

- get config from database
By `app/geetest.php` the field `server-get-config`, you can get your geetest id & and from database




## Thanks

[Germey/LaravelGeetest](https://github.com/Germey/LaravelGeetest)

## License

The MIT License (MIT).
