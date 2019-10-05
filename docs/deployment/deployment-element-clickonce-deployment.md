---
title: '&lt;Deployment&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
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
ms.openlocfilehash: 988ce0859ab24377395cc4077f9e6fa42e0487a5
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887855"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Deployment&gt; -Element (ClickOnce-Bereitstellung)
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
 Das `deployment` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v2` -Namespace. Das Element weist folgende Attribute auf.

| Attribut | Beschreibung |
|--------------------------| - |
| `install` | Erforderlich. Gibt an, ob diese Anwendung eine Anwesenheit im Windows- **Startmenü** und in der Systemsteuerung in der System **Steuerungsanwendung definiert** . Gültige Werte sind `true` und `false`. Wenn `false` `subscription` , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird immer die neueste Version dieser Anwendung aus dem Netzwerk ausgeführt, und das-Element wird nicht erkannt. |
| `minimumRequiredVersion` | Optional. Gibt die Mindestversion dieser Anwendung an, die auf dem Client ausgeführt werden kann. Wenn die Versionsnummer der Anwendung kleiner als die im Bereitstellungs Manifest angegebene Versionsnummer ist, wird die Anwendung nicht ausgeführt. Versionsnummern müssen im Format `N.N.N.N`angegeben werden, wobei `N` eine ganze Zahl ohne Vorzeichen ist. Wenn das `install` -Attribut `false`ist `minimumRequiredVersion` , darf nicht festgelegt werden. |
| `mapFileExtensions` | Optional. Wird standardmäßig auf `false` festgelegt. Gibt `true`an, dass alle Dateien in der Bereitstellung über die Erweiterung. Deployment verfügen müssen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Diese Erweiterung wird von entfernt, sobald Sie vom Webserver heruntergeladen wird. Wenn Sie die Anwendung mithilfe [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]von veröffentlichen, wird diese Erweiterung automatisch allen Dateien hinzugefügt. Mit diesem Parameter können alle Dateien in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung von einem Webserver heruntergeladen werden, der die Übertragung von Dateien blockiert, die mit "unsicheren" Erweiterungen wie z. b. exe enden. |
| `disallowUrlActivation` | Optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, wird verhindert, dass eine installierte Anwendung gestartet wird, indem Sie auf die URL klicken oder die URL in Internet Explorer eingeben. Wenn das `install` Attribut nicht vorhanden ist, wird dieses Attribut ignoriert. |
| `trustURLParameters` | Optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, kann die URL Abfrage Zeichen folgen Parameter enthalten, die an die Anwendung übermittelt werden, ähnlich wie Befehlszeilenargumente werden an eine Befehlszeilen Anwendung übermittelt. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Wenn das `disallowUrlActivation` -Attribut `true`ist `trustUrlParameters` , muss entweder aus dem Manifest ausgeschlossen oder explizit auf `false`festgelegt werden. |

 Das `deployment` -Element enthält auch die folgenden untergeordneten Elemente.

## <a name="subscription"></a>Abonnement
 Optional. Enthält das `update` -Element. Das `subscription` -Element weist keine Attribute auf. Wenn das `subscription` Element nicht vorhanden ist, wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Anwendung nie nach Updates suchen. Wenn das `install` -Attribut `deployment` des-Elements `false`ist, `subscription` wird das-Element ignoriert, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da eine vom Netzwerk gestartete Anwendung immer die neueste Version verwendet.

## <a name="update"></a>aktualisieren
 Erforderlich. Dieses Element ist ein untergeordnetes Element `subscription` des-Elements und enthält `beforeApplicationStartup` entweder das `expiration` -Element oder das-Element. `beforeApplicationStartup`und `expiration` können nicht im selben Bereitstellungs Manifest angegeben werden.

 Das `update` -Element weist keine Attribute auf.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 Optional. Dieses Element ist ein untergeordnetes Element `update` des-Elements und besitzt keine Attribute. Wenn das `beforeApplicationStartup` -Element vorhanden ist, wird die Anwendung bei [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] der Überprüfung auf Updates blockiert, wenn der Client online ist. Wenn dieses Element nicht vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sucht zuerst anhand der für das `expiration` Element angegebenen Werte nach Updates. `beforeApplicationStartup`und `expiration` können nicht im selben Bereitstellungs Manifest angegeben werden.

## <a name="expiration"></a>Ablauf
 Optional. Dieses Element ist ein untergeordnetes Element `update` des-Elements und hat keine untergeordneten Elemente. `beforeApplicationStartup`und `expiration` können nicht im selben Bereitstellungs Manifest angegeben werden. Wenn die Update Überprüfung stattfindet und eine aktualisierte Version erkannt wird, wird die neue Version zwischengespeichert, während die vorhandene Version ausgeführt wird. Die neue Version wird dann beim nächsten Start [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] der Anwendung installiert.

 Das `expiration` -Element unterstützt die folgenden Attribute.

|Attribut|Beschreibung|
|---------------|-----------------|
|`maximumAge`|Erforderlich. Gibt an, wie alt das aktuelle Update werden soll, bevor die Anwendung eine Überprüfung auf Aktualisierungen durchführt. Die Zeiteinheit wird durch das `unit` -Attribut bestimmt.|
|`unit`|Erforderlich. Gibt die Zeiteinheit für `maximumAge`an. Gültige Einheiten sind `hours`, `days`und `weeks`.|

## <a name="deploymentprovider"></a>deploymentProvider
 Für den .NET Framework 2,0 ist dieses Element erforderlich, wenn das Bereitstellungs Manifest einen `subscription` Abschnitt enthält. Für den .NET Framework 3,5 und höher ist dieses Element optional und wird standardmäßig auf den Server und den Dateipfad festgestellt, in dem das Bereitstellungs Manifest ermittelt wurde.

 Dieses Element ist ein untergeordnetes Element des `deployment` -Elements und weist folgende Attribute auf.

| Attribut | Beschreibung |
|------------| - |
| `codebase` | Erforderlich. Identifiziert den Speicherort als Uniform Resource Identifier (URI) des Bereitstellungs Manifests, das zum Aktualisieren der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung verwendet wird. Dieses Element ermöglicht außerdem das Weiterleiten von Update-Speicherorten für CD-basierte Installationen. Muss ein gültiger URI sein. |

## <a name="remarks"></a>Hinweise
 Sie können Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung so konfigurieren, dass Sie beim Start nach Updates sucht, nach Updates nach dem Start Suchen oder nie nach Updates sucht. Um beim Start nach Updates zu suchen, stellen Sie `beforeApplicationStartup` sicher, dass das `update` -Element unter dem-Element vorhanden ist. Stellen Sie sicher, dass das `expiration` -Element unter dem `update` -Element vorhanden ist und dass Aktualisierungsintervalle bereitgestellt werden, um nach dem Start nach Updates zu suchen.

 Entfernen Sie das-Element, um die `subscription` Überprüfung auf Updates zu deaktivieren. Wenn Sie im Bereitstellungs Manifest angeben, dass keine Updates überprüft werden sollen, können Sie mithilfe der <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> -Methode trotzdem manuell nach Updates suchen.

 Weitere Informationen zur Beziehung zwischen deploymentProvider und Updates finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Beispiele
 Das folgende Codebeispiel veranschaulicht ein `deployment` -Element in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] einem Bereitstellungs Manifest. Im Beispiel wird ein `deploymentProvider` -Element verwendet, um den bevorzugten Update Speicherort anzugeben.

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