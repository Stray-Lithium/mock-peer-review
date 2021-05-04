# Reviewing the candidates response 

Things to broadly look out for:
 - is the tone of the feedback positive/neutral?
 - is the feedback constructive and actionable?
 - is the feedback opinionated?
 - is there context to support or explain a position?
 - does their response provide space for a feedback loop?

 We're looking for someone who can constructively critique the code allowing the authoring developer to learn from the experience. 

 Also, can they markdown?

## Known issues... 
 - Single line comment at the top capturing purpose and use. Break down into more separate sections being more concise on both elements.
 - Capturing cli arguments in a non-defensive manor
 - Some param declared, some not (php)
 - Non declared param causes warning in non-human readable output (php)
 - Generally poor error handling
 - Parameter declaring throughout the file in a sporadic nature
 - Hardcoded file paths
 - Multiple use of hardcoded strings
 - No cache expiry
 - Poor variable labeling
 - Double loop through result set
 - Created a manual count of `t` where it can be counted using language functions
 - 'human readable' arg is non intuitive
 - 2 word param has unintended consequence
 - Inconstant indentation