# dalplatinum.github.io
No, I don't really know what I'm doing.  Why do you ask?

This is a basic canvas/javascript concoction that will display/animate words against a transparent background, for use on stream overlays and such.

url format is like ?words=<whatever you want it to say>&style=<style>
Style options are:
  		'vanilla',
		'arc',
		'bubbles',
		'solitaire',
		'stickmove',
		'bounce'
		'firework'
		'splats'
Or just leave the style bit off and get a random one.
I'll add more styles as I a) think of them, and b) learn how to make them work.
	
Three underscores will be replaced with a newline.  Because I couldn't think of any other way to do that.

If you are looking to use this in OBS, you can add it direct from here as a browser source - https://dalplatinum.github.io/?words=hello%20there
	
If you want to tie it to something like a chat trigger (I use '!p <words>') or a points redemption, you are going to need some automation software that will allow you to change properties on an OBS source.  I use LioranBoard receiver for this, and it is set up like:
	
	Add Button
	
	edit commands
	
	1. Action: String: Wildcard Pull
		variable: wordz
		wildcard number: 0
		turn to real: false
	
	2. Action: Source Change Settings
		sourcename: <name of your browser source>
		sourcesettings: {"url":"http://dalplatinum.github.io/?words=/$wordz$/"}
	
	Edit Twitch Triggers
		tick case-sensitive
		Message: !p *
	
So now if someone type '!p get in the sea' into my twitch channel, lioranboard will pick it up and change the URL of the browser source to http://dalplatinum.github.io/?words=get___in___the___sea.  In doing this, the page will reload and the animation will start.

There are other automation tools but I haven't used them, so can't comment.  As long as whatever you use can change the browser source URL property, you should be good to go.
	
You can also set up a browser source to only say a specific thing in a specific style, and just hide it and when you show it, the animation will kick off.

If it still doesn't work, find me and I'll help you out.  If I can.
	
TO-DO:
	
	Sort out scaling, because it goes horribly wrong at some resolutions.
	
	Add more effects
	
	Add image mode
	
	Add emoji
	
	Add Twitch Emotes/user profile pics
	
	Tidy up the code (comments/efficiency/redundancy)
	
	Add a 'simple' mode for people without dedicated GFX hardware
	
	
