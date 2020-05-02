	usage: split_audiobook.py [-h] [--search-dir] [--debug] [--delete]
		                      [-s SILENCE] [--silence-duration SILENCE_DURATION]
		                      [--dry] [--write-chapters] [-o] [--ignore-chapters]
		                      [--remove] [-q {low,normal,high,top}] [-l LENGTH]
		                      [-c CHAPTERS] [--activation-bytes ACTIVATION_BYTES]
		                      [--version]
		                      FILE [FILE ...]

	Splits large audiobook files into smaller parts which are then optionally
	encoded with Opus codec. Split points are either chapters defined in the
	audiobook, or supplied in external CSV file, or split happens in silence
	periods in approximately same distance (--length). Use --dry option to see how
	audio will be split, without actual conversion or --write-chapters to write
	chapters into separate file in simple csv format. Requires ffmpeg and ffprobe
	version v >= 2.8.11 Supports input formats m4a, m4b, mp3, aax (mka should also
	work but not tested)

	positional arguments:
	  FILE                  audiobook files

	optional arguments:
	  -h, --help            show this help message and exit
	  --search-dir          if FILE argument is directory it will recusivelly
		                    search for audio files and split them (default: False)
	  --debug               debug logging (default: False)
	  --delete              delete original file after split and conversion
		                    (default: False)
	  -s SILENCE, --silence SILENCE
		                    silence level in -x dB from max level (default: 30)
	  --silence-duration SILENCE_DURATION
		                    minimal duration of silence, default works fine, so
		                    change only, if necessary (default: 2)
	  --dry                 dry run, just prints calculated parts and exits
		                    (default: False)
	  --write-chapters      instead of spliting file, it just writes chapters into
		                    original_file.chapters csv file (default: False)
	  -o, --split-only      do not transcode, just split to parts using same audio
		                    codec (default: False)
	  --ignore-chapters     ignores chapters metadata, if they are pressent
		                    (default: False)
	  --remove              remove existing directory of splitted files (default:
		                    False)
	  -q {low,normal,high,top}, --quality {low,normal,high,top}
		                    opus codec quality params (default: high)
	  -l LENGTH, --length LENGTH
		                    duration of split segment in seconds (in case chapers
		                    are not available) (default: 1800)
	  -c CHAPTERS, --chapters CHAPTERS
		                    CSV file with chapters information, each line should
		                    contain: chapter_name,start_in_secs,end_in_secs
		                    (optionaly start and end can be in form hh:mm:ss.m)
		                    (default: None)
	  --activation-bytes ACTIVATION_BYTES
		                    activation bytes for aax format (default: None)
	  --version             shows version
