# median.pl

 #!usr/bin/perl -w
 
 #first to identify if there is a list or a file
  if (-e $ARGV[0]){
      @a=();
      open (IN, "<$ARGV[0]");
      while (<IN>){
      chomp($_);
      push (@a, $_);
      }
      close IN;
  } else {
       @a = @ARGV;
      }
 
 #make the data after re-arrangement (from small value to large) to be a new list
   @sa = sort {$a <=> $b} @a;
 
    print "@sa\n";
 
 #identify the median between even or odd-ordered lists
    if (($#sa+1)%2 == 0){
        $median = ( $sa[($#sa+1)/2-1] + $sa[($#sa+1)/2] )/2;
       }
 
    else {
       $median = $sa[$#sa/2];
   }

print "The median is $median. \n";
