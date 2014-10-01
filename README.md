# Raspberry Pi sonar

Having bought a sit/stand desk, we want to log the height that the desk is at. This will give us an idea if I'm using the desk as it should or if I start to lag after a while.

Initial code ultrasonic_2.py based on http://www.raspberrypi-spy.co.uk/2013/01/ultrasonic-distance-measurement-using-python-part-2/

Put this in your crontab to (a) let the sonar run once every minute between 8am and 8pm, and (b) automatically upload the last distance log to github at 11pm

    * 8-19 * * 1-5 sudo python /home/pi/sonar/ultrasonic_2.py >> /home/pi/sonar/distance_log.csv
    0 23 * * 1-5 cd /home/pi/sonar/ ; git add distance_log.csv ; git commit -m "Periodic update log" ; git push

## Todo

* Next step: only have this run when I'm actually behind my desk (e.g. using separate sonar pointing towards me)
