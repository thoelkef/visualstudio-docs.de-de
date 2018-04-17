---
title: '&lt;Bereitstellung&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 80bcba10c350cc61d582acb80321fc75e02f16ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Bereitstellung&gt; Element (ClickOnce-Bereitstellung)
Identifiziert die Attribute, die für die Bereitstellung von Updates und zum Verfügbarmachen für das System verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 Das `deployment`-Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1`-Namespace. Das Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`install`|Erforderlich. Gibt an, ob diese Anwendung eine Präsenz auf dem Windows-definiert **starten** Menü und in der Systemsteuerung **Software** Anwendung. Gültige Werte sind `true` und `false`. Wenn `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird immer die neueste Version dieser Anwendung vom Netzwerk gestartet, und erkennt die `subscription` Element.|  
|`minimumRequiredVersion`|Dies ist optional. Gibt die minimale Version dieser Anwendung, die auf dem Client ausgeführt werden kann. Wenn die Versionsnummer der Anwendung kleiner als die Versionsnummer im Bereitstellungsmanifest bereitgestellt ist, wird die Anwendung nicht ausgeführt. Versionsnummern müssen angegeben werden, im Format `N.N.N.N`, wobei `N` ist eine Ganzzahl ohne Vorzeichen. Wenn die `install` -Attribut ist `false`, `minimumRequiredVersion` darf nicht festgelegt werden.|  
|`mapFileExtensions`|Dies ist optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, alle Dateien in der Bereitstellung eine Erweiterung ".deploy" aufweisen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Diese Erweiterung wird von diesen Dateien entfernt werden, sobald es sie vom Webserver herunterlädt. Wenn Sie Ihre Anwendung mit veröffentlichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], er fügt diese Erweiterung automatisch auf alle Dateien. Dieser Parameter ermöglicht, alle Dateien innerhalb einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung von einem Webserver heruntergeladen werden, die Übertragung von Dateien, die "unsicheren" Erweiterungen wie z. B. .exe Endziffern blockiert.|  
|`disallowUrlActivation`|Dies ist optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, wird verhindert, dass eine installierte Anwendung durch Klicken auf die URL oder durch Eingabe der URL in Internet Explorer gestartet wird. Wenn die `install` -Attribut nicht vorhanden ist, wird dieses Attribut ignoriert.|  
|`trustURLParameters`|Dies ist optional. Wird standardmäßig auf `false` festgelegt. Wenn `true`, können Sie die URL kann Abfragezeichenfolgen-Parameter enthalten, die in die Anwendung übergeben werden, um eine befehlszeilenanwendung viel like Befehlszeilenargumente übergeben werden. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Wenn die `disallowUrlActivation` -Attribut ist `true`, `trustUrlParameters` müssen entweder aus dem Manifest ausgeschlossen oder explizit auf festgelegt `false`.|  
  
 Die `deployment` -Element enthält auch die folgenden untergeordneten Elemente.  
  
## <a name="subscription"></a>subscription  
 Dies ist optional. Enthält die `update` Element. Die `subscription` -Element weist keine Attribute. Wenn die `subscription` Element ist nicht vorhanden, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung nie nach Updates gesucht wird. Wenn die `install` Attribut des der `deployment` Element ist `false`, `subscription` Element wird ignoriert, da eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die immer über das Netzwerk gestartet wird, verwendet die neueste Version.  
  
## <a name="update"></a>aktualisieren  
 Erforderlich. Dieses Element ist ein untergeordnetes Element von der `subscription` Element und enthält entweder die `beforeApplicationStartup` oder `expiration` Element. `beforeApplicationStartup` und `expiration` darf nicht sowohl im gleichen Bereitstellungsmanifest angegeben werden.  
  
 Die `update` -Element weist keine Attribute.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Dies ist optional. Dieses Element ist ein untergeordnetes Element von der `update` Element und weist keine Attribute. Wenn die `beforeApplicationStartup` Element vorhanden ist, ist die Anwendung blockiert, wenn [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] für Updates überprüft werden, wenn der Client online ist. Wenn dieses Element nicht vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird für Updates, die auf Grundlage der Werte für die angegebene erster scan der `expiration` Element. `beforeApplicationStartup` und `expiration` darf nicht sowohl im gleichen Bereitstellungsmanifest angegeben werden.  
  
## <a name="expiration"></a>Ablaufdatum  
 Dies ist optional. Dieses Element ist ein untergeordnetes Element von der `update` -Element, und weist keine untergeordneten Elemente. `beforeApplicationStartup` und `expiration` darf nicht sowohl im gleichen Bereitstellungsmanifest angegeben werden. Bei die Überprüfung auf Updates und eine aktualisierte Version gefunden wird, speichert die neue Version während die vorhandene Version ausgeführt wird. Installiert die neue Version dann beim nächsten Start von der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
 Die `expiration` Element unterstützt die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`maximumAge`|Erforderlich. Gibt an, wie ALT die aktuellen Updates werden soll, bevor die Anwendung eine Prüfung auf Updates ausführt. Die Zeiteinheit richtet sich nach der `unit` Attribut.|  
|`unit`|Erforderlich. Identifiziert die Zeiteinheit für `maximumAge`. Gültige Einheiten sind `hours`, `days`, und `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Für .NET Framework 2.0 dieses Element ist erforderlich, wenn das Bereitstellungsmanifest enthält eine `subscription` Abschnitt. Für .NET Framework 3.5 und höher, wird dieses Element ist optional und wird standardmäßig auf den Server und den Dateipfad, in dem das Bereitstellungsmanifest ermittelt wurde.  
  
 Dieses Element ist ein untergeordnetes Element des `deployment`-Elements und weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`codebase`|Erforderlich. Identifiziert als Uniform Resource Identifier (URI) den Speicherort des Bereitstellungsmanifests, mit dem Aktualisieren, der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Mit diesem Element können auch zum Weiterleiten von Update-Speicherorte für die CD basierenden Installationen. Ein gültiger URI muss sein.|  
  
## <a name="remarks"></a>Hinweise  
 Sie können konfigurieren, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung zur Überprüfung auf Start, Suchen nach Updates nach dem Start oder nie nach Updates suchen. Um nach Updates beim Start zu scannen, sicher, dass die `beforeApplicationStartup` Element vorhanden ist, unter der `update` Element. Zum Scannen von Updates nach dem Start sicher, dass die `expiration` Element vorhanden ist, unter der `update` Element und die Updateintervallen angegeben werden.  
  
 Um die Überprüfung auf Updates zu deaktivieren, entfernen Sie die `subscription` Element. Bei der Angabe im Bereitstellungsmanifest nie nach Updates suchen, Sie können immer noch manuell nach Updates Suchen mithilfe der <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> Methode.  
  
 Weitere Informationen wie "deploymentProvider" auf Updates bezieht, finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Beispiele  
 Das folgende Codebeispiel veranschaulicht eine `deployment` Element in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Im Beispiel wird ein `deploymentProvider` Element, um die bevorzugte Updatepfad anzugeben.  
  
```  
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
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)