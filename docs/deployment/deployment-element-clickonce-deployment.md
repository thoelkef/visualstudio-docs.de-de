---
title: '&lt;Bereitstellung&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a7a22e683f1db05544f235308dc5ba495f74095
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629520"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Bereitstellung&gt; -Element (ClickOnce-Bereitstellung)
Identifiziert die Attribute, die für die Bereitstellung von Updates und zum Verfügbarmachen für das System verwendet werden.

## <a name="syntax"></a>Syntax

```xml

      <deployment
   install
   minimumRequiredVersion
   mapFileExtensions
   disallowUrlActivation
   trustUrlParameters
>
   <subscription>
         <update>
            <beforeApplicationStartup/>
            <expiration
               maximumAge
               unit
            />
         </update>
   </subscription>
   <deploymentProvider
      codebase
   />
</deployment>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `deployment` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1` -Namespace. Das Element weist folgende Attribute auf.


| Attribut | Beschreibung |
|--------------------------| - |
| `install` | Erforderlich. Gibt an, ob diese Anwendung eine Präsenz auf der Windows definiert **starten** Menü und in der Systemsteuerung **Software** Anwendung. Gültige Werte sind `true` und `false`. Wenn `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird immer die neueste Version dieser Anwendung aus dem Netzwerk ausgeführt und erkennt nicht die `subscription` Element. |
| `minimumRequiredVersion` | Dies ist optional. Gibt die minimale Version dieser Anwendung, die auf dem Client ausgeführt werden kann. Wenn die Versionsnummer der Anwendung kleiner als die Versionsnummer im Bereitstellungsmanifest angegeben ist, wird die Anwendung nicht ausgeführt. Versionsnummern müssen angegeben werden, im Format `N.N.N.N`, wobei `N` ist eine Ganzzahl ohne Vorzeichen. Wenn die `install` Attribut `false`, `minimumRequiredVersion` darf nicht festgelegt werden. |
| `mapFileExtensions` | Dies ist optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, alle Dateien in der Bereitstellung müssen eine Erweiterung ".deploy" aufweisen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] entfernt diese Erweiterung deaktivieren diese Dateien werden, sobald es vom Webserver herunterladen. Wenn Sie Ihre Anwendung mithilfe von veröffentlichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], es wird diese Erweiterung automatisch auf alle Dateien hinzugefügt. Mit diesem Parameter können alle Dateien innerhalb einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung von einem Webserver heruntergeladen werden, die Übertragung von Dateien mit der "unsicher" Erweiterungen wie .exe blockiert. |
| `disallowUrlActivation` | Dies ist optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, wird verhindert, dass eine installierte Anwendung durch Klicken auf die URL oder die Eingabe der URL in Internet Explorer gestartet wird. Wenn die `install` Attribut ist nicht vorhanden, die dieses Attribut wird ignoriert. |
| `trustURLParameters` | Dies ist optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, können Sie die URL kann Abfragezeichenfolgen-Parameter enthalten, die bei der Anwendung übergeben werden, viel wie Befehlszeilenargumente an eine befehlszeilenanwendung übergeben werden. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Wenn die `disallowUrlActivation` Attribut `true`, `trustUrlParameters` müssen entweder aus dem Manifest ausgeschlossen oder explizit auf festgelegt `false`. |

 Die `deployment` -Element auch die folgenden untergeordneten Elemente enthält.

## <a name="subscription"></a>subscription
 Dies ist optional. Enthält die `update` Element. Das `subscription` -Element weist keine Attribute auf. Wenn die `subscription` Element ist nicht vorhanden, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung nie nach Updates gesucht wird. Wenn die `install` Attribut der `deployment` Element ist `false`, `subscription` -Elements ignoriert, da eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die immer über das Netzwerk gestartet wird, verwendet die neueste Version.

## <a name="update"></a>aktualisieren
 Erforderlich. Dieses Element ist ein untergeordnetes Element des der `subscription` Element und enthält entweder die `beforeApplicationStartup` oder `expiration` Element. `beforeApplicationStartup` und `expiration` können nicht beide im gleichen Bereitstellungsmanifest angegeben werden.

 Das `update` -Element weist keine Attribute auf.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Dies ist optional. Dieses Element ist ein untergeordnetes Element des der `update` Element und weist keine Attribute. Wenn die `beforeApplicationStartup` Element vorhanden ist, wird die Anwendung blockiert, wenn [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sucht nach Updates, wenn der Client online ist. Wenn dieses Element nicht vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scannt zunächst nach Updates, die basierend auf die Werte für die `expiration` Element. `beforeApplicationStartup` und `expiration` können nicht beide im gleichen Bereitstellungsmanifest angegeben werden.

## <a name="expiration"></a>Ablauf
 Dies ist optional. Dieses Element ist ein untergeordnetes Element des der `update` -Element, und hat keine untergeordneten Elemente. `beforeApplicationStartup` und `expiration` können nicht beide im gleichen Bereitstellungsmanifest angegeben werden. Wenn die Überprüfung auf Updates tritt ein, und eine aktualisierte Version gefunden wird, werden die neue Version zwischengespeichert, während die vorhandene Version ausgeführt wird. Installiert die neue Version dann beim nächsten Start von der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.

 Die `expiration` Element unterstützt die folgenden Attribute.

|Attribut|Beschreibung|
|---------------|-----------------|
|`maximumAge`|Erforderlich. Gibt an, wie ALT das aktuelle Update werden soll, bevor die Anwendung eine Prüfung auf Updates ausführt. Die Zeiteinheit richtet sich nach der `unit` Attribut.|
|`unit`|Erforderlich. Gibt die Zeiteinheit für `maximumAge`. Gültige Einheiten sind `hours`, `days`, und `weeks`.|

## <a name="deploymentprovider"></a>deploymentProvider
 Für .NET Framework 2.0, dieses Element ist erforderlich, wenn das Bereitstellungsmanifest enthält eine `subscription` Abschnitt. Für .NET Framework 3.5 und höher, wird dieses Element ist optional und wird standardmäßig mit dem Server und Pfad der Datei, die in der das Bereitstellungsmanifest erkannt wurde.

 Dieses Element ist ein untergeordnetes Element des `deployment` -Elements und weist folgende Attribute auf.


| Attribut | Beschreibung |
|------------| - |
| `codebase` | Erforderlich. Identifiziert den Speicherplatz, als ein Uniform Resource Identifier (URI), der das Bereitstellungsmanifest, das zum Aktualisieren von der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieses Element ermöglicht es auch für die Weiterleitung der Speicherorte für die Aktualisierung für Installationen von CD-basierte. Ein gültiger URI muss sein. |

## <a name="remarks"></a>Anmerkungen
 Sie können konfigurieren, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung für die Suche nach Updates beim Start nach Updates suchen, nach dem Start oder nie nach Updates suchen. Stellen Sie sicher, die für die Suche nach Updates beim Start der `beforeApplicationStartup` Element vorhanden ist, unter der `update` Element. Suche nach Updates nach dem Start sicher, dass die `expiration` Element vorhanden ist, unter dem `update` -Element, und die Updateintervallen angegeben werden.

 Zum Suchen nach Updates zu deaktivieren, entfernen Sie die `subscription` Element. Bei der Angabe im Bereitstellungsmanifest nie nach Updates gesucht, Sie können weiterhin manuell nach Updates Suchen mithilfe der <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> Methode.

 Weitere Informationen zur Beziehung wie "deploymentProvider" zu Updates finden Sie unter [Auswählen einer Strategie der ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Beispiele
 Das folgende Codebeispiel veranschaulicht eine `deployment` Element in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Im Beispiel wird eine `deploymentProvider` Element, um den bevorzugten Updatepfad anzugeben.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)