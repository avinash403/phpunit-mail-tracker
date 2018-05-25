# phpunit-mail-tracker
Makes it real easy to write unit test cases for emails in laravel


### Installation by Composer

	$ composer require php-imap/php-imap


### Usage example

```php

//import MailTracker trait
import MailTracker\MailTracker
import Mail;

class ExampleTest extends TestCase
{
	//include trait in the test class
	use MailTracker;

	public function test_mail_fiveMailsAreSent()
	{
		$message = 'What a wonderful day';
		
		$emailAddresses = [
					'testone@test.com',
					'testtwo@test.com', 
					'testthree@test.com',
					'testfour@test.com',
					'testfive@test.com'
				]

		foreach($emailAddresses as $emailAddress){
			
			Mail::raw($message, function(){
			
				$message->to($emailAddress)->subject('Greetings');
			
			});
		}

		//assert number of mails which were sent
		$this->assertEmailCount(5);
	}
}
```	

### Available assertions
* assertEmailCount
* assertEmailWasSent

## Currently not in production ##

### Contribute on github
clone this repository( https://github.com/avinash403/phpunit-mail-tracker.git ), make your changes and raise a pull request to development branch