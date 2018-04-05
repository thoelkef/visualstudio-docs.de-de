## <a name="create-a-kubernetes-development-environment-in-azure"></a>Erstellen einer Kubernetes-Entwicklungsumgebung in Azure
In Connected Environment können Sie auf Kubernetes basierende Umgebungen erstellen, die vollständig von Azure verwaltet werden und für die Entwicklung optimiert sind. Der Befehl erstellt eine Umgebung namens `mydevenvironment` in `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Unterstützte Gebietsschemas: `eastus`, `westeurope`

> [!Note]
> Dieser Befehl dauert etwa sechs Minuten. Sie können mit dem Leitfaden fortfahren, ohne auf den Abschluss des Befehls warten zu müssen.
