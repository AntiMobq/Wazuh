# Wazuh
Integration Scripts

# SSH Channeling
  Configuração da ossec.conf (Arquivo de comportamento do agente)

```xml
<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/auth.log</location>
</localfile>
```

  Para funcionamento prévio escolhi a integração com auditd
```bash
  sudo apt install auditd
```

 Edite **/etc/audit/rules.d/audit.rules** e adicione:
 ```xml
  -w /var/run/utmp -p wa -k session
  -w /var/log/lastlog -p wa -k session
  ```

  E no ossec.conf
```xml
<localfile>
  <log_format>audit</log_format>
  <location>/var/log/audit/audit.log</location>
</localfile>
```

Na maquina **sudo systemctl restart wazuh-agent**. No manager **sudo systemctl restart wazuh-manager**
