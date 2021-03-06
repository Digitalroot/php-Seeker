php-Seeker
==========

Seeker is a PHP class that lets you search text files from the CLI 

Purpose:
==========

        At my work we are sent hundreds of fixed length text files containing 
        data about cars. There are times when we need to find and reprocess 
        at least some of the data we are sent. Searching by hand for these 
        records is a pain. So I wrote a php script to make my life easier.


How does it work?

        The Seeker object is very flexible. Please review the following 
        for different examples on how to use it. 


Examples: (See example.php also.)

    echo '----- Single Vin, Single Location -----' . "\n";

    $Seeker = new Seeker();
    $Seeker->mNeedle = '1GCEC0000000E6772';
    $Seeker->mHayStack = 'searchDir';
    $Seeker->sResultFile = 'Result.txt';
    $Seeker->Search();

    echo "\n" . '----- Multi Vin, Single Location -----' . "\n";

    $SearchFor[] = '1HGCM000000005818';
    $SearchFor[] = 'WDBKK000000088377';
    $SearchFor[] = '1N4AL000000069647';

    $Seeker = new Seeker();
    $Seeker->mNeedle = $SearchFor;
    $Seeker->mHayStack = 'searchDir';
    $Seeker->sResultFile = 'Result.txt';
    $Seeker->Search();

    unset($SearchFor); // Clean up

    echo "\n" . '----- Single Vin, Multi Location -----' . "\n";

    $SearchDir[] = 'searchDir';
    $SearchDir[] = 'searchDir2';

    $Seeker = new Seeker();
    $Seeker->mNeedle = '1GCEC000000036772';
    $Seeker->mHayStack = $SearchDir;
    $Seeker->sResultFile = 'Result.txt';
    $Seeker->Search();

    unset($SearchDir); // Clean up

    echo "\n" . '----- Multi Vin, Multi Location -----' . "\n";

    $SearchFor[] = '1HGCM600000005818';
    $SearchFor[] = 'WDBKK400000008377';
    $SearchFor[] = '1N4AL100000009647';

    $SearchDir[] = 'searchDir';
    $SearchDir[] = 'searchDir2';

    $Seeker = new Seeker();
    $Seeker->mNeedle = $SearchFor;
    $Seeker->mHayStack = $SearchDir;
    $Seeker->sResultFile = 'Result.txt';
    $Seeker->Search();

    unset($SearchFor); // Clean up
    unset($SearchDir); // Clean up

    echo "\n" . '----- FileList Vin, Single Location -----' . "\n";

    $Seeker = new Seeker();
    $Seeker->mNeedle = 'vin.txt';
    $Seeker->mHayStack = 'searchDir';
    $Seeker->sResultFile = 'Result.txt';
    $Seeker->Search();

    echo "\n" . '----- FileList Vin, Multi Location -----' . "\n";

    $SearchDir[] = 'searchDir';
    $SearchDir[] = 'searchDir2';

    $Seeker = new Seeker();
    $Seeker->mNeedle = 'vin.txt';
    $Seeker->mHayStack = $SearchDir;
    $Seeker->sResultFile = 'Result.txt';
    $Seeker->Search();

    unset($SearchDir); // Clean up
