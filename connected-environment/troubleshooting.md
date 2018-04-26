---
title: Problembehandlung | Microsoft-Dokumentation
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: troubleshooting
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: b41d228bcced6149c95b09b2445dd656ed9772d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-guide"></a>Anleitung zur Problembehandlung

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Fehler 'upstream connect error or disconnect/reset before headers' (Upstream-Verbindungsfehler oder Verbindung vor den Headern trennen bzw. zurücksetzen.)
Dieser Fehler wird möglicherweise angezeigt, wenn Sie versuchen, auf Ihren Dienst zuzugreifen. Dies kann passieren, wenn Sie in einem Browser zur URL eines Diensts navigieren. 

**Grund:** Der Containerport ist nicht verfügbar. Der Fehler tritt am häufigsten aus folgenden Gründen auf: 
* Der Container ist noch nicht vollständig erstellt und bereitgestellt. Dies kann vorkommen, wenn Sie `vsce up` ausführen oder den Debugger starten und Sie dann versuchen, auf den Container zuzugreifen, bevor dieser vollständig bereitgestellt wurde.
* Die Portkonfiguration ist in Ihrer Dockerfile-Datei, Ihrem Helm-Diagramm und in anderem Servercode, der Ports öffnet, nicht einheitlich.

**Mögliche Lösung:**
1. Wenn der Container gerade erstellt bzw. bereitgestellt wird, können Sie 2-3 Sekunden warten und anschließend versuchen, erneut auf den Dienst zuzugreifen. 
1. Überprüfen Sie Ihre Portkonfiguration. Die angegebenen Portnummern sollten in allen nachfolgend aufgeführten Objekten **identisch** sein:
    * **Dockerfile:** Angegeben von der `EXPOSE`-Anweisung.
    * **[Helm-Diagramm](https://docs.helm.sh):** Angegeben von den Werten `externalPort` und `internalPort` eines Diensts, die häufig in einer `values.yml`-Datei gespeichert sind.
    * Ports, die in Anwendungscode, z.B. in Node.js, geöffnet werden: `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>Die Konfigurationsdatei wurde nicht gefunden
Wenn Sie `vsce up` ausführen, wird der folgende Fehler angezeigt: `Config file not found: .../vsce.yaml`

**Grund:** `vsce up` muss über das Stammverzeichnis des Codes ausgeführt werden, den Sie ausführen möchten, und der Codeordner muss initialisiert worden sein, damit er mit Connected Environment funktioniert.

**Mögliche Lösung:**
1. Ändern Sie Ihr aktuelles Stammverzeichnis in den Stammordner, der Ihren Dienstcode enthält. 
1. Wenn in dem Codeordner keine vsce.yaml-Datei enthalten ist, führen Sie `vsce init` aus, um Docker, Kubernetes und VSCE-Objekte zu generieren.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Fehler: 'The pipe program 'vsce' exited unexpectedly with code 126.' (Das Pipeprogramm „vsce“ wurde unerwartet mit Code 126 beendet.)
Dieser Fehler kann manchmal entstehen, wenn Sie den VS Code-Debugger starten. Es handelt sich dabei um einen Programmfehler.

**Mögliche Lösung:**
1. Schließen Sie Visual Studio Code, und starten Sie das Programm neu.
2. Drücken Sie erneut auf F5.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Debugfehler 'Configured debug type 'coreclr' is not supported' (Der konfigurierte Debugtyp „coreclr“ wird nicht unterstützt.)
Wenn der Visual Studio Code-Debugger ausgeführt wird, wird der Fehler `Configured debug type 'coreclr' is not supported.` ausgelöst.

**Grund:** Die Visual Studio Code-Erweiterung für Connected Environment ist nicht auf Ihrem Entwicklungscomputer installiert.

**Mögliche Lösung:** Installieren Sie die [Visual Studio Code-Erweiterung für Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Im Azure-Portal werden keine Connected Environment-Instanzen angezeigt

**Grund:** Im Azure-Portal ist noch keine Vorschauversion von Connected Environment vorhanden.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>Der Typ- oder Namespacename „MyLibrary“ konnte nicht gefunden werden

**Grund:** Der Buildkontext ist standardmäßig auf Projekt- bzw. Dienstebene festgelegt. Aus diesem Grund wird das Bibliotheksprojekt, das Sie verwenden, nicht gefunden.

**Mögliche Lösung:**
1. Ändern Sie die vsce.yaml-Datei, um den Buildkontext auf Projektmappenebene festzulegen.
2. Ändern Sie die Dockerfile- und Dockerfile.develop-Dateien, um korrekt auf die CSPROJ-Dateien zu verweisen, die im Zusammenhang mit dem Buildkontext stehen.
3. Platzieren Sie eine DOCKERIGNORE-Datei neben der SLN-Datei, und verändern Sie diese bei Bedarf.

Ein Beispiel finden Sie unter https://github.com/sgreenmsft/buildcontextsample.

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Autorisierungsfehler 'Microsoft.ConnectedEnvironment/register/action' beim Erstellen einer Umgebung.
Möglicherweise wird der folgende Fehler angezeigt, wenn Sie eine Umgebung verwalten und Sie in einem Azure-Abonnement arbeiten, mit dem Sie nicht über Berechtigungen für Besitzer oder Mitwirkende verfügen.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Grund:** Für das ausgewählte Azure-Abonnement ist der Microsoft.ConnectedEnvironment-Namespace nicht registriert.

**Mögliche Lösung:** Ein Benutzer, der über Berechtigungen für Besitzer oder Mitwirkende auf das Azure-Abonnement verfügt, kann den folgenden Azure CLI-Befehl ausführen, um den Microsoft.ConnectedEnvironment-Namespace manuell zu registrieren:

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE verwendet meine Dockerfile-Datei nicht, um einen Container zu erstellen 

**Grund:** VSCE kann so konfiguriert werden, dass dieser Dienst auf eine bestimmte Dockerfile-Datei in Ihrem Projekt zeigt. Wenn Sie den Eindruck haben, dass Visual Studio Connected Environment nicht die Dockerfile-Datei verwendet, die Sie zum Erstellen von Containern vorgesehen haben, müssen Sie diesem Dienst explizit sagen, wo diese Datei liegt. 

**Mögliche Lösung:** Öffnen Sie die `vsce.yaml`-Datei, die von Visual Studio Connected Environment in Ihrem Projekt generiert wurde. Verwenden Sie die `configurations->develop->build->dockerfile`-Anweisung, um auf die Dockerfile-Datei zu zeigen, die Sie verwenden möchten:

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```