## <a name="initialize-code-for-docker-and-kubernetes-development"></a>Initialisieren von Code für die Entwicklung in Docker und Kubernetes
Bisher haben Sie eine einfache Web-App erstellt, die lokal ausgeführt werden kann. Im Folgenden containerisieren Sie diese App, indem Sie Objekte erstellen, die den Container der App und die Art und Weise definieren, wie sie auf Kubernetes bereitgestellt wird. Das ist mit Connected Environment einfach: 

1. Starten Sie Visual Studio Code, und öffnen Sie den Ordner `webfrontend`. (Sie können die Standardaufforderungen zum Hinzufügen von Debugobjekten oder Wiederherstellen des Projekts ignorieren.)
1. Öffnen Sie das integrierte Terminal in Visual Studio Code (mithilfe des Menüs **Ansicht | Integriertes Terminal**).
1. Führen Sie den folgenden Befehl aus (stellen Sie sicher, dass **webfrontend** Ihr aktueller Ordner ist):

```cmd
vsce init --public
```

Der Befehl ```init``` der CLI von Connected Environment erstellt Docker- und Kubernetes-Objekte mit Standardeinstellungen:
* `./Dockerfile` beschreibt das Containerimage der App, und wie der Quellcode erstellt und in dem Container ausgeführt wird.
* Ein [Helm chart (Helm-Diagramm)](https://docs.helm.sh) unter `./charts/webfrontend` beschreibt, wie der Container für Kubernetes bereitgestellt wird.

Sie müssen den gesamten Inhalt dieser Dateien noch nicht verstehen. Es ist jedoch erwähnenswert, dass **die gleichen Konfigurationscodeobjekte für Kubernetes und Docker für die Entwicklung bis zur Produktion verwendet werden können, womit über verschiedene Umgebungen hinweg eine höhere Konsistenz gewährleistet wird.**
 
Durch den Befehl `init` wird ebenfalls eine Datei namens `./vsce.yaml` erstellt. Dies ist die Konfigurationsdatei für Connected Environment. Sie ergänzt die Docker- und Kubernetes-Artefakte mit zusätzlicher Konfiguration, die die iterative Entwicklung in Azure ermöglicht. Das Helm-Standarddiagramm stellt beispielsweise keine öffentlichen Endpunkte zur Verfügung. In manchen Situationen ist es jedoch hilfreich, während der Entwicklung einen öffentlichen Endpunkt vorübergehend zu öffnen, damit Sie Ihren Code testen können, z.B. mit einem mobilen Gerät oder einer Webhook-URL. Eine mit `init --public` erstellte „vsce.yaml“-Datei überschreibt die Helm-Standardparameter, um einen öffentlichen Endpunkt nur während der Entwicklungszeit zur Verfügung zu stellen.
