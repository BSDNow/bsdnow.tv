
On your discussion of periodic [#445], you missed some options that I immediately set on any new install:

daily_show_success="NO"         # scripts returning 0
weekly_show_success="NO"        # scripts returning 0
security_show_success="NO"      # scripts returning 0

This significantly improves the signal-to-noise ratio of the periodic notifications. Daily "nothing to see here" messages are quickly disabled/discarded/ignored; actual "this is not what I expected" messages are quite useful.
