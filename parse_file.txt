with open('events/ancestors_story.txt') as fp:
	line = fp.readline()
	cnt = 1
	text = ""
	while line:		
		print("Line {}: {}".format(cnt, line.strip()))
		if line.startswith('# ACS'):
			text = "%s\r\n%s" % (text, line)
		line = fp.readline()
		cnt += 1

	with open('EVENTS.md', 'w+') as ev:
		ev.write(text)
