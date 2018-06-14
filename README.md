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

- Code Examples

```
    $dtt = 0.79 ; // Density actual
    $tem = 28 ; // Temperature (*C)
    $gal = 1000 ; // Gallons

    $data = Tool::convert($dtt,$tem,$gal); // convert

   dd($data); 
  //array:5 [
  //  "D15" => 0.7995
  //  "VCF" => 0.9879
  //  "WCF" => 0.7984
  //  "LIT" => 76.8254
  // "KG" => 60.5952
  //]
```
  
  