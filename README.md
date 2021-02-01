# Keine-ahnung
Pvp

/* 
Based on the Java version by Minho:
https://code.sololearn.com/cU3pPEPkOK37/?ref=app
*/

using System;
using System.Collections.Generic;
using System.Linq;

using static System.Console;

class Palindrone {
  static Func<string, string> 
    Reverse = s => new string(
      s.Reverse().ToArray());

  static Func<string, bool> 
    Is = s => s == Reverse(s);
    
  static Func<string, string> 
    Make = s => $"{s}{Reverse(s)}";
    
  static Action<string, bool>
    Print = (s, isPalendrome) =>    
      WriteLine(isPalendrome
        ? $"{s} is a palindrome.\n"
        : @$"{s} is NOT a palindrome.
Making it palindrome -> {Make(s)}
");

  static Action<string>
    Run = w => Print(w, Is(w));

  static void Main(string[] args) {
    (new List<string>{
      "001", "121", "100", "1234321",
      "123456789", "0025665200"
    }).ForEach(Run);
  }
}
