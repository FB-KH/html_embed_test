```python
class Config(configparser.SafeConfigParser):
    def __init__(self, path):
        configparser.SafeConfigParser.__init__(self, os.environ)
        self.read(path)

    def getShotgunURL(self):
        return self.get("shotgun", "server")

    def getEngineScriptName(self):
        return self.get("shotgun", "name")

    def getEngineScriptKey(self):
        return self.get("shotgun", "key")

    def getEngineProxyServer(self):
        try:
            proxy_server = self.get("shotgun", "proxy_server").strip()
            if not proxy_server:
                return None
            return proxy_server
        except configparser.NoOptionError:
            return None
```


{::comment}
https://github.com/FB-KH/html_embed_test/blob/main/_pages/sgeventdaemon_snippet.md
{:/comment}

*[configparser]: Just testing to see this feature works