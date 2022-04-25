Create a cron job with:

*/5 * * * * <path to scrip>/failsafe.sh >> /var/www/test.log

`
#!/bin/bash
running_ps=$(ps aux | grep queue)
needle='artisan queue'
if [[ "$running_ps" != *"$needle"* ]]; then
	echo "restarting"
	cd /var/www/html/<path to project> && php artisan queue:work &
else
	echo "already working"
fi


`
