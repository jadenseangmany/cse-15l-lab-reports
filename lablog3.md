# Lab 3 Bugs and Commands
## Part 1: Bugs
### Code:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
Here I chose the method "reversed" where it's supposed to reverse an array given any length of an array. For example, an array of {1,2,3} is supposed to return {3,2,1}.
### Faliure Inducing Input:
```
@Test
  public void testReversed() {
    int[] input1 = {1,2,3};
    assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input1));
  }
```
Here, the failure inducing input is really any value other than an input array of all zeroes, but I chose {1,2,3} as my failure inducing input.
### Input that does not induce a failure:
```
@Test
  public void testReversed() {
    int[] input1 = {0,0,0};
    assertArrayEquals(new int[]{0,0,0}, ArrayExamples.reversed(input1));
  }
```
The code is broken so that only an empty array would work, so this input of {0,0,0} actually runs successfully and does not induce a failure.
### Symptom
![Symptom](images/symptoms-lab3.png)
Here is what happens when I try to run the test. There is one failure and one pass, where the failure is when I input the {1,2,3} array.
### Before and After
Before:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

After:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
## Part 2: Researching Commands

### Search for multiple patterns with `-e`

  1. 

  ```
(base) rain@Rains-MacBook-Air 911report % grep -e "Bin Ladin" -e "Obama" chapter-10.txt
                    Bin Ladin;
                Pakistan and Afghanistan." The paper took it as a given that Bin Ladin would
                therefore detailed specific U.S. demands for the Taliban: surrender Bin Ladin and
                Bin Ladin. Shortly thereafter, President Bush authorized broad new authorities for
                administration knew that theTaliban was unlikely to turn over Bin Ladin.
                out that Bin Ladin resented the secularism of Saddam Hussein's regime. Finally, the
                memo said, there was no confirmed reporting on Saddam cooperating with Bin Ladin on
                at the same time-not only Bin Ladin. Secretary Rumsfeld later explained that at the
            President Bush argued that the new war went beyond Bin Ladin." Our war on terror
                and lightly governed frontier provinces. As of July 2004, Bin Ladin and Zawahiri are
```

  Explanation: Here, I used the -e option to specify multiple search patterns. I used the patterns "Bin Ladin" and "Obama" to find all the lines that match with "Bin Ladin" and "Obama". It's useful to search for multiple things at the same time, so I don't have to do two separate searches.

  2. 
  
  ```
  (base) rain@Rains-MacBook-Air 911report % grep -e "password" -e "key" chapter-6.txt    
                gathering money and supplies. With Abu Hoshar, he recruited inTurkey and Syria as
                Afghanistan, and at least one key member swore loyalty to Bin Ladin. But the cell's
                key perpetrators of the attack to al Qaeda. The CIA listed the key suspects,
                identifying, recruiting, clearing, and obtaining Senate confirmation of key
                pass intelligence to Bush and some of his key advisers.
                confirmation of key officials, particularly at the Defense Department.
                broader regional policy." Two key decisions that had been deferred, he noted,
                conflict (SOLIC), the key counterterrorism policy office in the Pentagon-never
                Tenet ticked off key questions: What is the chain of command? Who takes the shot?
  ```
  Explanation: Here's another example where I used the patterns "password" and "key" to search the `chapter-6.txt` file for those keywords. This could possibly be useful when trying to search through a large file or a number of different files for a password or key. Unfortunately, this output didn't render anything useful, but it could be useful for other certain circumstances.

### Invert match with `-v`

  1.

  ```
(base) rain@Rains-MacBook-Air 911report % grep -v "a" chapter-6.txt

    
        
            FROM THREAT TO THREAT
            
            
            
            THE MILLENNIUM CRISIS
            
            
            
            
                    Deek.
            
            
            
            
            
            
                    countries.
            
            
            
            
            
            
            
            
            
            
                    ferry.
            
            
            
            
            
            
            
            
            
            
            
            
            
                independent.
            
            
            
            
            
            
            
            
            
            
            
                    Angeles.
            
            
            POST-CRISIS REFLECTION: AGENDA FOR 2000
            
                    home.
            
            
            
                did not.
            
            
            
            
            
                trip to the region.
            
            
            
            
            
            
            
                    counterterrorism.
            
            
                    unit]."
            
            
            Berger met twice with Tenet in April to try to resolve the dispute. The Deputies
            
                    frozen.
            
            
            
                terrorist funding.
            
            
            
            
                    flows.
            
            
            
                of Congress.
            
            
            Border Security
            
            They included 
            
                
                        proceedings;
                
                        terrorism;
                
                
            
            
                        origin.
                
            
            
            
            
            
            
                    risky.
            
            
            
            
            
            
            
            
                    out.
            
            
            
            
            
            
            
            THE ATTACK ON THE USS COLE
            
            
                    Aden.
            
            
            
            
            
            
            
            
            
            
                more well-known.
            
            
            
            
            
            
            
                directed the bombing.
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            CHANGE AND CONTINUITY
                president in 2001.
            From the Old to the New
            
            
            
            
                    process.
            
            
            
                the NSC.
            
            
            
                Counterterrorism Security Group functioned.
            
            
            
            
            
            
            
            
                    responses." Before Vice President Cheney visited the
                responsible" for the Cole.
            
            
            
                    this.
            
            
                    CIA.
            
                the review very soon.
            
            
                (NSPD) on terrorism.
            
            
            
            
            
                    terrorism.
            
            THE NEW ADMINISTRATION'S APPROACH
            
            
            
            
                policy process did not follow through quickly enough.
            
            
            
                    2006.
            
                expressed it to her, Rice told us.
            
            
            
            
            
            
            
            
                    concluded.
            
            
                    victory.
            
            
            
            
            
                    Berger.
            
            
            
            
            
            
            
                rights to fly over neighboring countries.
            
            
                this mission," Rice told us.
            
            
            
            
            
            
                Robert Mueller, took office just before 9/11. The
            
            
            
            
            
                this concern.
            
            
            
                    he.
            
                moving vehicle.
            
                    herself.
            
                on these issues.
            
            
                Jumper told us, problems with the equipment persisted. Nevertheless, the Air Force
                    this."
            
            September 2001
            
            
                be in order[.]"
            
            
                Rice, Tenet, Rumsfeld, or someone else would give the order to fire.
            
                with little discussion.
            
                    work.
            
                spring of 2002.
            
            
            
            
            
            
            
            
  ```

  Explanation: Here, I used the -v option, which returns all the lines that do not match the pattern I provide. In this example, I provided the pattern "a", so grep returned all the lines that do not have the letter "a". This could be useful when looking for more broad strings that filters out things that we don't want.

  2. 
  
  ```
(base) rain@Rains-MacBook-Air Env_Prot_Agen % grep -v "e" tech_sectiong.txt







banking.






acidic � not acidic.



and without updating.
  ```
  Explanation: In this example, we returned all the lines that do not have the letter "e" in the `tech_sectiong.txt` file. As e is the most common vowel, we notice that there were not much lines with text returned, which creates a very interesting output.

### Show line number with `-n`

  1..
  2..

### Highlight matches with `--color` and `less -R`

  1..
  2..


