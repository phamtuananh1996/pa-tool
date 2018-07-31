# pa-tool
- Public excel : `php artisan vendor:publish --tag=seed`
- init data T53B : `php artisan gfl-seed:T53B`
- init data T54B : `php artisan gfl-seed:T54B`
- init data T56B : `php artisan gfl-seed:T56B`
- Public config : `php artisan vendor:publish --tag=config`

- After you have installed PA tool, open your Laravel config file config/app.php and add the following lines.
In the $providers array add the service providers for this package.

  `GFL\Tool\ToolServiceProvider::class,`

- Add the facade of this package to the $aliases array.

  `'Tool' => GFL\Tool\Facades\ToolFacade::class,`

-Code simple convert

```
    $density_actual = 0.79 ; // Density actual
    $Temperature = 28 ; // Temperature (*C)
    $volumn = 1000 ; // Volumn
    $unit_volumn = 'gallon'; // gallon , lit

    $data = Tool::convert($density_actual,$Temperature,$volumn,$unit_volumn); // simple convert

    dd($data); 
  //array:5 [
  //  "D15" => 0.7995
  //  "VCF" => 0.9879
  //  "WCF" => 0.7984
  //  "LIT" => 76.8254
  //  "KG" => 60.5952
  //]
```

- Code convert

```
    $density_actual = 0.79 ; // Density actual
    $Temperature = 28 ; // Temperature (*C)
    $volumn = 1000 ; // Volumn
    $unit_volumn = 'gallon'; // gallon , lit
    $exchange_rate = 25000 ; // exchange rate
    $price = 20000; //price
    $unit_price = 'VND/Gallon'; // VND/Gallon, USD/Gallon
    $vat = 20 ; // %
    $data = Tool::convert($density_actual,$Temperature,$volumn,$unit_volumn,$exchange_rate,$price,$unit_price,$vat); // convert

   dd($data); 
  //array:8 [
  //  "D15" => 0.7995
  //  "VCF" => 0.9879
  //  "WCF" => 0.7984
  //  "LIT" => 76.8254
  //  "KG" => 60.5952
  //  "sub_amount" => 123456,
  //  "vat" => 123456,
  //  "amount" => 123456
  //]
```
  
  