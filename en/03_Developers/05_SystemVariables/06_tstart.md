### EvoCMS start time

float tstart

Contains the start time of EvoCMS in the "unix time" format, allowing you to estimate the page generation time.

#### Example

    <?php  
    $time = $modx->tstart;  
    echo strftime("%H:%M:%S", $time);  
    // returns "17:56:10"  
    ?>
