# Leak report

The one memory leak I found was from the use of calloc in the strip function.

To fix this memory leak we need to free the "cleaned" variable at the end of the "is-clean" function. The reason we free that variable is because it uses the "result" variable from "strip" which is what calls calloc in the first place. Also "cleaned" is not used by anything inside main therefore we must free it at the end of "is-clean".

Note: We also need to add an empty string check for "cleaned" that just returns "result == 0" if cleaned is empty because free apparently doesn't play nice with empty strings.

