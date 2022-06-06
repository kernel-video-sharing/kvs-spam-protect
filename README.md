# kvs-spam-protect

KVS Spamming Protect by Akismet (same of wordpress)



## Install 

```shell

composer require fyrts/akismet

```


## Using

```php

# blocks/feedback/feedback.php
# line 11 add

        // Spam Protect By Akismet
        require_once $config["project_path"]."/vendor/autoload.php";
        $akismet = new \Akismet\Akismet('YOU KEY', 'https://youdomains.com'); //$status = $akismet->verifyKey();
        $comment = new \Akismet\Comment();
        $comment->setAuthorEmail($email)->setContent($message); //->setAuthor('Author Name')->setUserIp('46.161.11.82')->setReferrer($referrer)
        $result = $akismet->check($comment);    // Check for spam
        //var_dump($result);
        if ($result->isSpam) {
            $errors_async[] = array('error_code' => 'spam', 'block' => 'feedback');
            $errors['code'] = 2;
        }
        if ($result->isDiscardable) {
            $errors_async[] = array('error_code' => 'spam', 'block' => 'feedback');
            $errors['code'] = 2;
        }


 

```