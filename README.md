# zabbix-minecraft-monitoring
Provides to put TPS and online to zabbix (only local minecraft servers)

## About
- This is fork from https://github.com/garelp/zabbix-minecraft-server

## Requirements

- Zabbix server 5x or above
- Minecraft server with support [Skript plugin](https://github.com/SkriptLang/Skript/releases)
- I use this with Grafana 9 (optional)

## Quick start
- Edit path to Skript plugin in `minecraft.conf` 
- Put `minecraft.conf` to `/etc/zabbix/zabbix_agentd.d/` and run `systemctl restart zabbix-agent`
- Then put `zabbix.sk` in `plugins/Skript/scripts` (if you don't have this folder - install [plugin](https://github.com/SkriptLang/Skript/releases) for your minecraft server version)
- `sk reload zabbix` in minecraft console
- Go to your Zabbix and import Template, then attach this to your host
- You're done!

## Troubleshooting

- Error in zabbix `tail permission denied`, in this case the best solution - add user `zabbix` to needed group, ex. - `usermod -aG minecraft zabbix` (where `minecraft` - group of user, where exist minecraft server, `zabbix` - user of zabbix-agent)

## Finally
- You can erase old logs periodically, just put this to crontab `0 7 * * * rm -f /path/to/server/plugins/Skript/logs/*.log`
- You can use this with grafana like this:
![Monitoring minecraft server with Grafana 9](https://i.imgur.com/8qKGXHG.png)
