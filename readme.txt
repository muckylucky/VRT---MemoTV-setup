 _____      _ _ _                  _                            _               
/  ___|    | | (_)                | |                          (_)              
\ `--.  ___| | |_  __ _  ___ _ __ | |_    _____  _____ _ __ ___ _ ___  ___  ___ 
 `--. \/ _ \ | | |/ _` |/ _ \ '_ \| __|  / _ \ \/ / _ \ '__/ __| / __|/ _ \/ __|
/\__/ /  __/ | | | (_| |  __/ | | | |_  |  __/>  <  __/ | | (__| \__ \  __/\__ \
\____/ \___|_|_|_|\__, |\___|_| |_|\__|  \___/_/\_\___|_|  \___|_|___/\___||___/
                   __/ |                                                        
                  |___/      

# Excercise: VRT - MemoTV setup
# Difficulty: Medium
# Install: acampaignwc.emsecure.local/portal :: Ask for a login if you don't own one
# Install version: V5 - V6
# Estimation: Make a prediction on how long it will take to complete this project
# Note: Every exercise should be treated as a real life project, somebody will be apointed to act as the customer and/or colleague.
		Construct a professional and correct e-mail with your questions towards the customer and e-mail them to the apointed person.
		Functional questions for a colleague can be asked at will, providing that the apointed person is not occupied with something else.

# Summary:

	Mock up images:
		- images/image001.png
		- images/image002.png
		- images/image003.png

	For the front-end, only the part with the blue marking should be created inside the selligent tool. We are able to iFrame the HTML. So design wise this will not be the most difficult project, however in the backend we expect a lot more:

		- Between 2 voting periods only the percentage will be shown to the users. They will not have the option to vote, so there will be no voting button. During voting periods we would like to see the percentage and the voting button.
		- We decided to keep the voting anonymous (there are no prices to be collected from this). However we had some issues in the past with hackers, so we would like a system that limits the amount of votes from 1 IP to 100.

	Weekly flow
	-----------
		- Phase 1: Voting
		- Wednesday morning – Monday 12:00h

		Anon votes via the programpage MemoTv, where the votingform is embedded in an iFrame.
		The voting percentage should be displayed on the fly, you will already see it before you even vote.
		When you press on a voting button, the other buttons should be disabled (this can be done by giving them a lighter color). This way the people can see what they just voted on. We would also like to show a small thank you text on top of the page after voting.
		Monday 12:00h the voting will be closed automatically and SIM will send out an e-mail to a fixed e-mail address (bs@selligent.com) with the following results:

			- The winning program (the most votes)
			- The programs that will be passed to the next week (rest of the votes)
			- The losing program (the least votes)

	Weekly flow
	-----------
		- Phase 2: The results
		- Monday 12:00h – Wednesday morning (07:00h)

		Only the results should be displayed, voting isn’t possible anymore.

	Weekly flow
	-----------
		- Cycle continues back to phase 1 etc.

		The movies to vote on come from a playlist, the sequence is fixed because they should match the playlists. We want Selligent to handle as much automatically as possible:
			- Closing and mailing Monday at 12:00h
			- Clearing votes or starting new ones on Wednesday morning
			- There are 2 different methods that we can use for the voting options
				o Or we enter the titles weekly in a table in selligent
				o Or Selligent reads the articles from an JSON feed of the playlist.
				example: http://mp.vrt.be/api/playlist/collection_113.json 
				We prefer this option.
			- The flow should be able to skip weeks, the results of the previous voting should be shown longer on the page
			- The results of the week should be stored in a separate DB, with programtitles (from selligent of the JSON feed) en the amount of votes (absolute and percentage), we would like to gather statistics from these numbers.

	Extra
	-----
		- We're not able to change the JSON structure
		- Here are the widths for the page (view images/image003.png)
		- Use SIM functions to read the JSON file and to make adjustments, don't use jQuery for this

	2e part of the excercise
	------------------------
		- Create a webservice in C# that has the title of the video as input and based upon that input checks if it is part of the live JSON feed
			- This way we can prevent invalid votes from passing through the system
			- Call this webservice by using SIM functionality only

