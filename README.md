# Issues-I-had-when-Installing-Matconvent-Python
Issues I experinced when I was trying to install VOT+Matconvent + Python


+ Visual Studio 2017 doesnt work with Matlab 2017b in case of installing Matconvent
+ Instead use VS2015

+ Dont forget to add CUDNN to CUDA9.0
+ Becarful after you add CUDNN python doesnt work.

+ To explore which compiler you want to use (VS2017, VS2015) in case you have both just type in matab  mex -setup 
  it allows you to choose one.
  
  VOT and TRAX installation
  =========================
  
1. I downloaded TRAX from here https://github.com/alessiodore/trax
2. Replace every xchange by change if any
3. Vot toolkit/ tracker/ System_wrapper.m I added this line before line#176 

#Instead of# :
	    [status, output] = system(tracker.commandcomand, '');
#ADD#
            command= string(sprintf('python %s', tracker.command));
	    [status, output] = system(command, '');
        
 4. In Trax.py add import fuctools
 5. At line 392   
 #instead of#
            assert(reduce(lambda x,y: x and y, [isinstance(p,tuple) for p in points], False))
 #Add#
            assert(functools.reduce(lambda x,y: x and y, [isinstance(p,tuple) for p in points], False))
         
 6. If map function doesnt have lenth add list before map.
 
 7. The same for all trax files (e.g. images, Region,...)
 


 
        
        
  
   
