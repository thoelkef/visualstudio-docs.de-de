## <a name="clean-up"></a>Bereinigen
Verwenden Sie den Befehl `vsce env rm` zum vollständigen Löschen einer Connected Environment-Umgebung in Azure, einschließlich aller Dienste, die darin ausgeführt werden. Beachten Sie, dass dieser Vorgang nicht rückgängig gemacht werden kann.

Im folgenden Beispiel wird Connected Environment in Ihrem aktiven Azure-Abonnement aufgelistet, und die Umgebung „myenv“ in der Ressourcengruppe „myenv-rg“ wird gelöscht.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

