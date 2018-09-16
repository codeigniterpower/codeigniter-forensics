# CodeIgniter - Profiler

Powered complete replacement for the CodeIgniter Profiler. 

Will convert the static and very limited debug information of the original "profiler" 
into a powered bar toggeable with very more debuggin information that not inhury your configured 
view loaded of your projects.
Forensics is a **high-powered, extended bebugger, completely replacement** very customizable 
for the CodeIgniter Profiler.

## FEATURES:

- **Reflects for debug All variables sent to the view** and easyle shown in the bar.
- **SQL detailed look of queries** indicating controller location, with support for illuminate/database
- **Reflects list of all files loaded at request/response** including their location (relative to your FCPATH).
- **Featured Console class library** with hability to track memory in your project. 
- **Profiler output completely skinnable.** by reading the comments in the Profiler class before. 

## INSTALLING

Comes included with CodeigniterPowered, but for CI 2 or CI3:

**Requirements**

* Codeigniter 2.x or 3.x

**Manual controlled install**

**1)** Located your Codeigniter proyect and then download the repository at the `Applications` root directory

`wget https://github.com/codeigniterpower/codeigniter-profiler/archive/master.tar.gz -O codeigniter-profiler.tar.gz`

**2)** Extract the contents or place the files into your applications directory root, this must be 4 files inside:

* `config/Profiler.php` 
* `libraries/Profiler.php`
* `libraries/Console.php`
* `views/profiler_template.php`

**3)** Then, just enable the profiler like normal.
    
`$this->output->enable_profiler(true);`

Now the output wil be a **little flame at the botton right corner** on each load request/response, 
click on it and see the new profiler.


## CONFIGURATION

Wil be located at the `config/profiler.php` file, and heres the documentation:

* `$config['uri_string']           = TRUE;` will show the loaded files section tab at the profiler bar
* `$config['view_data']            = TRUE;` will show the data vars section tab at the profiler bar:
  * `$config['config']               = TRUE;` added info of configuration variables in data section.
  * `$config['controller_info']      = TRUE;` added info of controller on each request/response
  * `$config['get']                  = TRUE;` added info of GET data at the data variables section
  * `$config['post']                 = TRUE;` added info of the post varaibles at the data vars section
  * `$config['http_headers']         = TRUE;` added info of server headers at the data variables section
* `$config['queries']              = TRUE;` will show the sql DBMS information section tab in the profiler bar
  * `$config['eloquent']             = FALSE;` added info eloquent sql related information in the SQL DBMS section
  * `$config['query_toggle_count']   = 50;` will provide limit of amount of information of the querys to show
* `$config['benchmarks']          = TRUE;` will show benchmarks section, false disable it.
* `$config['memory_usage']         = TRUE;` will show the memory section tab in the profiler bar
* `$config['console']               = TRUE;` will show console library feature section

You can change the location of the profiler bar by changing the `$bar_location` variable 
at the top of the *profiler_template* view to one of the following locations: 
`top-right`, `top-left`, `bottom-left`, `bottom-right`, `top`, `bottom`.

## USAGE

**As configuration said, it has 6 sections** On each request and response, a new icon will be displayed in the right botton corner, a little flame, 
just click it and a new debug bar with a lot of info will be displayed.

### Sections

* **Files loading** at last right side, when click it, will show each php file and order in witch are 
included and requested by the proyect.
* **Data vars** second from right to left, when click it, will show server vars, session data, get 
and post data, and all the variables parsed to the views in he second parameter, if that view was 
loaded with that array of parameters no matter what view are loaded/used.
* **Sql DBMS querys** the center section in the forensic profiler, easyle will show all the querys 
made by the **current requested controller**, (but not all of ruted controllers) of the database's 
still in use.
* **Memory** will show the memory usage, total amount by the scripts, details only will show if you 
use the `Console::log_memory` from the foresic logging featured.
* **time and Benchmarks** this tab will show same information of the "Benchmarks" section of the normal 
old profiler behaviour.
* **Console section**, this are explained detailed in next:

### Console library

In addition to the normal information that CI's Profiler provides, you now have two new logging commands at your disposal that work with the Forensics Profiler:

* `Console::log($data)`: This function accepts any data type and simply creates a pretty, readable output of the variable, using `print_r()`. Very handy for logging where you are in the script execution, or outputting the contents of an array, the resulting poutput will be in the new 'console' tab at the new 'profiler' in the botton right corner.
* `Console::log_memory($variable, $name)` makes possible track the memory usage by the variables of the scripts, In order to use either of these functions, you must be sure to load the Console library before you use it, usage are of two ways:
  * When no parameters are passed in, it will record the current memory usage of your script. This is perfect for watching a loop and checking for memory leaks. The log memory will output in the new 'memory' tab at the new 'profiler' in the botton right corner.
  * If you pass in the `$variable` and `$name` parameters, will output the amount of memory that variable is using to the console.


### Illuminate Database Queries

In addition to CodeIgniter database queries, Forensics can **display any queries run by [Illuminate Database](https://github.com/illuminate/database) models or the Eloqeunt query builder**. To enable this feature, change the config setting for `eloquent` in `config/profiler.php`. If you're using Illuminate Database in your project, note that this feature requires `Capsule\Manager`.

# Credits

The default look, and some of the additional functionality, was heavily inspired by ParticleTree's [PHP Quick Profiler](http://particletree.com/features/php-quick-profiler/).

Original proyect : https://github.com/lonnieezell/codeigniter-forensics
