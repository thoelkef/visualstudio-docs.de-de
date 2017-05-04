---
title: "Anwendungsmanifeste f&#252;r Office-Projektmappen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio]"
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Anwendungsmanifeste f&#252;r Office-Projektmappen
  Ein Anwendungsmanifest ist eine XML\-Datei, die die Assemblys beschreibt, die in einer Microsoft Office\-Projektmappe geladen werden. Die Microsoft Office\-Entwicklungstools in Visual Studio verwenden das [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Anwendungsmanifestschema, das in der [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)\-Referenz definiert ist.  
  
 Anwendungsmanifeste für Office\-Projektmappen verwenden die folgenden [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Elemente und \-Attribute.  
  
|Element|Beschreibung|Attribute|  
|-------------|------------------|---------------|  
|[&#60;assembly&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assembly-element-clickonce-application.md)|Erforderlich. Ein Element der obersten Ebene.|`manifestVersion`|  
|[&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assemblyidentity-element-clickonce-application.md)|Erforderlich. Gibt die primäre Assembly der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Anwendung an.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; Element &#40;ClickOnce Application&#41;](~/deployment/trustinfo-element-clickonce-application.md)|Gibt die Sicherheitsanforderungen der Anwendung an.|Keine|  
|[&#60;entryPoint&#62; Element &#40;ClickOnce Application&#41;](~/deployment/entrypoint-element-clickonce-application.md)|Erforderlich. Gibt den Einstiegspunkt des Anwendungscodes für die Ausführung an.|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60;dependency&#62; Element &#40;ClickOnce Application&#41;](~/deployment/dependency-element-clickonce-application.md)|Erforderlich. Gibt jede Abhängigkeit an, die für die Ausführung der Anwendung erforderlich ist. Gibt optional Assemblys an, die vorinstalliert werden müssen.|Keine|  
|[&#60;file&#62; Element &#40;ClickOnce Application&#41;](~/deployment/file-element-clickonce-application.md)|Erforderlich. Gibt jede Nicht\-Assemblydatei an, die von der Anwendung verwendet wird. Kann COM\-Isolationsdaten \(Component Object Model\) enthalten, die der Datei zugeordnet sind.|`name`<br /><br /> `size`|  
  
 Anwendungsmanifeste für Office\-Projektmappen verwenden das folgenden Element im `co.v1`\-Elemente.  
  
```  
<entryPoint> <co.v1:customHostSpecified /> </entryPoint>   
```  
  
 Diese Anwendungsmanifeste weisen auch die folgenden Elemente und Attribute im `vstav3`\-Namespace auf.  
  
```  
<addIn> <entryPointsCollection> <entryPoints> <entryPoint> </entryPoint> </entryPoints> </entryPointsCollection> <update></update> <postActions> <postAction> <postActionData> </postActionData> <postAction> </postActions> <application> <customizations> <customization> </customization> </customizations> </application </addIn>  
```  
  
|Element|Beschreibung|Attribute|  
|-------------|------------------|---------------|  
|[&#60;customHostSpecified&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Erforderlich. Markiert das Manifest ausdrücklich als Office\-Projektmappe.|Keine|  
|[&#60;addin&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Erforderlich. Speichert Einstiegspunkte in einem einzelnen Namespace.|Keine|  
|[&#60;entryPointsCollection&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Erforderlich. Gruppiert alle Assemblys für eine oder mehrere Office\-Projektmappen.|`id`|  
|[&#60;entryPoints&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Erforderlich. Gruppiert alle Assemblys, die in einer Office\-Projektmappe ausgeführt werden.|Keine|  
|[&#60;entryPoint&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Erforderlich. Gibt die Assemblys an, die in einer Office\-Projektmappe ausgeführt werden.|`class`<br /><br /> `contract`|  
|[&#60;update&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Erforderlich. Konfiguriert Updates für die Projektmappe.|`enabled`<br /><br /> `expiration`|  
|[&#60;postActions&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Optional. Gruppiert alle Aktionen nach der Bereitstellung, die nach der Installation von Office\-Projektmappen ausgeführt werden.|Keine|  
|[&#60;postAction&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Optional. Gibt eine Aktion nach der Bereitstellung an.|Keine|  
|[&#60;postActionData&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Optional. Konfiguriert Daten für eine Aktion nach der Bereitstellung.|Keine|  
|[&#60;application&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Erforderlich. Umschließt die anwendungsspezifischen Informationen in einem einzelnen Knoten.|Keine|  
|[&#60;customizations&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Erforderlich. Speichert alle anwendungshostspezifischen Informationen in einem separaten Namespace.|Keine|  
|[&#60;customization&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Erforderlich. Speichert anwendungshostspezifische Informationen in einem separaten Namespace.|`xmlns`|  
|[&#60;document&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Nur für Projektmappen auf Dokumentebene erforderlich. Speichert anpassungsspezifische Informationen.|`solutionId`|  
|[&#60;appAddin&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Nur für Projektmappen auf Anwendungsebene erforderlich. Speichert anpassungsspezifische Informationen.|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Optional. Speichert den Namen des VSTO\-Add\-Ins, das in der Liste der installierten VSTO\-Add\-Ins angezeigt wird.|Keine|  
|[&#60;description&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Nur für VSTO\-Add\-Ins erforderlich. Speichert die Beschreibung, die in der Liste der installierten Programme angezeigt wird.|Keine|  
|[&#60;formRegions&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Nur für Outlook\-VSTO\-Add\-Ins erforderlich, die Formularbereiche enthalten.|Keine|  
|[&#60;formRegion&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Nur für Outlook\-VSTO\-Add\-Ins erforderlich, die Formularbereiche enthalten.|`Name`|  
|[&#60;vstoRuntime&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Erforderlich. Beschreibt eine bestimmte Version der Visual Studio Tools for Office\-Laufzeit, die von der Office\-Projektmappe unterstützt wird.|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## Hinweise  
 Anwendungs\- und Bereitstellungsmanifeste in Office\-Projektmappen können manuell bearbeitet werden. Anschließend müssen Sie die Anwendung und die Bereitstellungsmanifeste mit dem Tool zur Generierung und Bearbeitung von Manifesten \(„mage.exe“ und „mageui.exe“\) erneut signieren. Weitere Informationen finden Sie unter [How to: Re-sign Application and Deployment Manifests](~/deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Dateiort  
 Ein Anwendungsmanifest ist für eine einzelne Version einer Projektmappe spezifisch. Aus diesem Grund müssen die Anwendungsmanifeste getrennt von Bereitstellungsmanifesten gespeichert werden.[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] platziert die versionsspezifischen Dateien in einem Unterverzeichnis, das gemäß der zugewiesenen Version im Unterverzeichnis **Application Files** im Ordner „Publish“ benannt wird.  
  
## Dateinamensyntax  
 Der Name einer Anwendungsmanifestdatei muss den vollständigen Namen und die Erweiterung der Anwendung, wie im `assemblyIdentity`\-Element angegeben, gefolgt von der Erweiterung „.manifest“ aufweisen. Beispielsweise würde ein Anwendungsmanifest, das auf die „OutlookAddIn1.dll“\-Anpassung verweist, die folgende Syntax für den Dateinamen verwenden.  
  
 `OutlookAddIn1.dll.manifest`  
  
## Siehe auch  
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  