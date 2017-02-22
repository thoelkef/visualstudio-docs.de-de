---
title: "&lt;deployment&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> element [ClickOnce deployment manifest]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;deployment&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert die Attribute, die für die Bereitstellung von Updates und zum Verfügbarmachen für das System verwendet werden.  
  
## Syntax  
  
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
  
## Elemente und Attribute  
 Das `deployment`\-Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1`\-Namespace.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`install`|Erforderlich.  Gibt an, ob für diese Anwendung ein Eintrag im **Startmenü** von Windows und in der Systemsteuerung unter **Software** vorhanden ist.  Gültige Werte sind `true` und `false`.  Wenn der Wert `false` lautet, führt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] immer die neueste Version dieser Anwendung vom Netzwerk aus und erkennt das `subscription`\-Element nicht.|  
|`minimumRequiredVersion`|Optional.  Gibt die Mindestversion dieser Anwendung an, die auf dem Client ausgeführt werden kann.  Wenn die Anwendung eine niedrigere als die im Bereitstellungsmanifest angegebene Versionsnummer aufweist, wird die Anwendung nicht ausgeführt.  Versionsnummern müssen im Format `N.N.N.N` angegeben werden, wobei `N` eine ganze Zahl ohne Vorzeichen ist.  Wenn das `install`\-Attribut den Wert `false` hat, muss `minimumRequiredVersion` nicht festgelegt werden.|  
|`mapFileExtensions`|Optional.  Übernimmt den Standardwert `false`.  Wenn der Wert `true` ergibt, müssen alle Dateien in der Bereitstellung die Erweiterung ".deploy" besitzen.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] entfernt diese Erweiterung von diesen Dateien, sobald es sie vom Webserver herunterlädt.  Wenn Sie eine Anwendung mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veröffentlichen, wird diese Erweiterung automatisch allen Dateien hinzugefügt.  Mit diesem Parameter können alle Dateien innerhalb einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung von einem Webserver heruntergeladen werden, der die Übertragung von Dateien mit "unsicheren" Dateierweiterungen wie EXE blockiert.|  
|`disallowUrlActivation`|Optional.  Übernimmt den Standardwert `false`.  Falls `true`, wird verhindert, dass eine installierte Anwendung durch Klicken auf die URL oder durch Eingabe der URL in Internet Explorer gestartet wird.  Wenn das `install`\-Attribut nicht vorhanden ist, wird dieses Attribut ignoriert.|  
|`trustURLParameters`|Optional.  Übernimmt den Standardwert `false`.  Falls `true`, kann die URL Abfragezeichenfolgen\-Parameter enthalten, die ähnlich an die Anwendung übergeben werden, wie Befehlszeilenargumente an eine Befehlszeilenanwendung übergeben werden.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von Abfragezeichenfolgen\-Informationen in einer Online\-ClickOnce\-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Wenn das `disallowUrlActivation`\-Attribut den Wert `true` hat, muss `trustUrlParameters` entweder aus dem Manifest ausgeschlossen oder explizit auf `false` festgelegt werden.|  
  
 Das `deployment`\-Element enthält außerdem die folgenden untergeordneten Elemente.  
  
## Abonnement  
 Optional.  Enthält das `update`\-Element.  Das `subscription`\-Element weist keine Attribute auf.  Wenn das `subscription`\-Element nicht vorhanden ist, sucht die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung nie nach Updates.  Weist das `install`\-Attribut des `deployment`\-Elements den Wert `false` auf, wird das `subscription`\-Element ignoriert, da eine vom Netzwerk gestartete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung immer die neueste Version verwendet.  
  
## update  
 Erforderlich.  Dieses Element ist ein untergeordnetes Element des `subscription`\-Elements und enthält entweder das `beforeApplicationStartup`\-Element oder das `expiration`\-Element.  `beforeApplicationStartup` und `expiration` können beide nicht im gleichen Bereitstellungsmanifest angegeben werden.  
  
 Das `update`\-Element weist keine Attribute auf.  
  
## beforeApplicationStartup  
 Optional.  Dieses Element ist ein untergeordnetes Element des `update`\-Elements und weist keine Attribute auf.  Wenn das `beforeApplicationStartup`\-Element vorhanden ist, wird die Anwendung blockiert, während [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nach Updates sucht, sofern der Client online ist.  Wenn das Element nicht vorhanden ist, sucht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zunächst nach Updates auf Basis der für das `expiration`\-Element angegebenen Werte.  `beforeApplicationStartup` und `expiration` können beide nicht im gleichen Bereitstellungsmanifest angegeben werden.  
  
## expiration  
 Optional.  Dieses Element ist ein untergeordnetes Element des `update`\-Elements und verfügt über keine untergeordneten Elemente.  `beforeApplicationStartup` und `expiration` können beide nicht im gleichen Bereitstellungsmanifest angegeben werden.  Wenn die Updateüberprüfung auftritt und eine aktualisierte Version erkannt wird, wird die neue Version zwischengespeichert, während die vorhandene Version ausgeführt wird.  Die neue Version wird dann beim nächsten Start der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installiert.  
  
 Das `expiration`\-Element unterstützt die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`maximumAge`|Erforderlich.  Gibt an, wie alt die aktuelle Version werden soll, bevor die Anwendung nach Updates sucht.  Die Zeiteinheit wird durch das `unit`\-Attribut bestimmt.|  
|`unit`|Erforderlich.  Identifiziert die Zeiteinheit für `maximumAge`.  Gültige Einheiten sind `hours`, `days` und `weeks`.|  
  
## deploymentProvider  
 Für .NET Framework 2.0 ist dieses Element erforderlich, wenn das Bereitstellungsmanifest einen `subscription`\-Abschnitt enthält; andernfalls optional.  Dieses Element ist für .NET Framework 3.5 und höher optional. Standardmäßig werden der Server und der Dateipfad verwendet, in denen das Bereitstellungsmanifest gefunden wurde.  
  
 Dieses Element ist ein untergeordnetes Element des `deployment`\-Elements und verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`codebase`|Erforderlich.  Identifiziert als Uniform Resource Identifier \(URI\) den Speicherort des Bereitstellungsmanifests, das verwendet wird, um die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung zu aktualisieren.  Diese Angabe ermöglicht auch das Weiterleiten von Updatepfaden für CD\-basierte Installationen.  Muss ein gültiger URI sein.|  
  
## Hinweise  
 Sie können die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung so konfigurieren, dass sie beim Start, nach dem Start oder nie nach Updates sucht.  Damit beim Start nach Updates gesucht wird, muss das `beforeApplicationStartup`\-Element als untergeordnetes Element des `update`\-Elements vorhanden sein.  Damit nach dem Start nach Updates gesucht wird, muss das `expiration`\-Element als untergeordnetes Element des `update`\-Elements vorhanden sein, und die gewünschten Updateintervalle müssen angegeben werden.  
  
 Um die Suche nach Updates zu deaktivieren, entfernen Sie das `subscription`\-Element.  Auch wenn Sie im Bereitstellungsmanifest angeben, dass nie nach Updates gesucht werden soll, können Sie trotzdem mit der <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>\-Methode manuell nach Updates suchen.  
  
 Weitere Informationen zur Beziehung von deploymentProvider zu Updates finden Sie unter [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## Beispiele  
 Im folgenden Codebeispiel wird ein `deployment`\-Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest veranschaulicht.  Im Beispiel wird ein `deploymentProvider`\-Element verwendet, um den bevorzugten Updatepfad anzugeben.  
  
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
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)