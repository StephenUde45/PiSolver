# PI Solver Code

# Libraries
import math
import random

# Generate random coordinates (a, b) within the unit square                        
def getRandomPoint():
   xmult = round( random.random() )
   ymult = round( random.random() )
   a = random.random()
   b = random.random()

    # Determine whether to negate the coordinates based on rounding
   if( xmult ):
      a *= -1
   if( ymult ):
      b *= -1

    # Calculate the Euclidean distance from the origin
   c = math.sqrt( (a * a) + (b * b) )
   return c

def dartThrow( inHits ):
# Simulate a dart throw, check if the point is within the unit circle
   if( getRandomPoint() < 1.0 ):
      return inHits + 1
   else:
      return inHits

def main():
   hits = 0
   # Prompt user for the number of darts to throw
   numberOfDarts = int( input( "\n   Enter the number of darts to throw: ") )

   # Check if the number of darts is sufficient
   if( numberOfDarts < 1000 ):
      print( "   You need more than 1000 darts.  Try again.\n\n" )
   else:
      i = 0
      # Perform the dart throw simulation
      while( i < numberOfDarts ):
         hits = dartThrow( hits )
         i += 1
         
      # Calculate the approximation of PI
      approxPI = 4.0 * (float( hits ) / float( numberOfDarts ) )
      # Output the real value of PI and the approximation
      print( "\n      Real value of PI: ", math.pi)
      print( "   Approximation of PI: ", approxPI )
# Run the main function
main()
