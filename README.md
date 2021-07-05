#Election_Analysis

**Overview of election audit analysis – project purpose and scope:**
  The election commission of Colorado requested additional data to complete the recent election audit for a race conducted in 3 counties with 3 candidates.  Requested was:
  
  1.The voter turnout for each county
  
  2.The percentage of votes from each county out of the total count and 
  
  3.The county with the highest turnout

**Election-Audit Results**

Based on the output we can review in the text file (election.analysis.txt)  The analysis was completed using the following code examples to get these results.
**Total or Number of votes cast:  369,711**

1.  Initially the ability to count the votes was determined using the initialize sequence:
#Initialize a total vote counter.
total_votes = 0
  
2.  A for loop was started through the data rows to total the votes.  This was the first step needed to analyze the rest of the data.
For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1
This was printed to the text file using the variable total_votes:
3.Save the results to our text file.
with open(file_to_save, "w") as txt_file:

    # Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        
**Breakdown of number of votes and the percentage of total votes for each county in the precinct:**
  1.  Jefferson County voters cast a total of 38,655 votes with 10.5% of the total election votes.

	2.  Denver County voters cast 306,055 votes with 82.8% of the total votes and
  
 3. Arapahoe County cast 24,801 votes with 6.7% of the total votes
 
1.  I went back into the For loop discussed in point 1 to gather the county name 
3: Extract the county name from each row.
	        county_name = row[1]
          
2.  and to add to the list of county names using an if statement if a new county was found in the list that was unique using the append command.  This assured no votes were missed.  
 Write an if statement that checks that the
	        county does not match any existing county in the county list.
        if county_name not in county_options:     
	
	            4b: Add the existing county to the list of counties.
            county_options.append(county_name) 
	            4c: Begin tracking the county's vote count.
	            county_votes[county_name] = 0	        
              5: Add a vote to that county's vote count.
	        county_votes[county_name] +=1
	-The results of these commands were output to the text file:
Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")
	3.  Following the total vote and match to county routine, a percentage was requested and an additional for loop was created and a similar command to write to the text file to show the results:
  
Write a for loop to get the county from the county dictionary.
    for county_name in county_options:
        
        # 6b: Retrieve the county vote count.
        votes = county_votes[county_name]
       
        # 6c: Calculate the percentage of votes for the county.
        vote_percentage = float(votes) / float(total_votes) * 100

         # 6d: Print the county results to the terminal.
        county_results = (f"{county_name}: {vote_percentage:.1f}% ({votes:,})\n")
        print(county_results)
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
        
**County with the largest number of votes:**
The county with the largest number of votes was Denver County.

1.  To find the county with the largest turnout, there was an if statement written with the new variable identified early in the program, “Highvote_votes” and “highvote_county” and “highvote_percentage” that if the county total was higher than the other candidates that this would be shown as the winner

 '''Write an if statement to determine the winning county and get its vote count.
        if (votes > highvote_votes):
            highvote_votes = votes
            highvote_county = county_name
            highvote_percentage = vote_percentage'''
**Breakdown of the number of votes and percentage of total votes each candidate received**

Candidate Stockham received 85,213 votes and 23.0% of the votes.

Candidate DeGette received 272,892 votes and 73.8% of the total vote and candidate Doane received 11,606 votes or 3.1% of the votes.

1.  The code for each candidate in the for loop asked to get the vote counts and percentage and to show the vote percentage by dividing votes by total votes and showing the output using an fstring to capture from the libraries of candidate_name and the vote_percentage.  This was then output to the text file.

Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)

        print(votes)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        Print each candidate's voter count and percentage to the
        terminal.
        print(candidate_results)
        Save the candidate results to our text file.
        txt_file.write(candidate_results)
        
        
**Which candidate won the election, vote count and percentage of votes:**  
Candidate DeGette received the highest number of votes with a total of 272,892 votes and 73.8% of the total vote. 

1.  To find the winner an If statement that if the votes were the greatest of the candidates for count, and percentage it would print.
 Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage
            
***Election-Audit Summary***

This code can be applied to any election if the csv data set is formatted similarly.  It can run for any election as the variables count  include the “.append” command to add counties and candidates.  This is a key feature of this code because it will not eliminate any data for county or candidate.  The current voting concerns of miscounting elections would be reduced with this feature.  This code also provides an output that is easy to read as the variables of county and candidate are clearly defined instead of “candidate_1” or “county_1”.  The remainder of the code is set up for calculation ease and speed.
Additional coding can be provided to enhance the deliverable to widen its capabilities.  
1.	 To further develop an analysis in the current concerns of voter counting, the election officials may want to know the percentage of votes divided by the total registered voters to determine voter turnout for the election.  This would be done by including the variable of “total_valid_voters” placing similar steps as we did to find the candidates’ percentages.
2.	If the Commission desired a variable in the data set of the precinct where the votes were cast could be added to identify candidate winner per precinct and to look at percentage of voter turnout for a precinct.  This data could be sold to political groups wishing to improve the efficiency of their campaigns and offer additional revenue to the state by seling these data sets.


