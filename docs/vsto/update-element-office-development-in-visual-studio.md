---
title: "&lt;update&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "update-Element"
  - "<update>-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <update>-Element"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# &lt;update&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `update`\-Element gibt das Intervall an, in dem die Projektmappe nach Aktualisierungen sucht.  
  
## Syntax  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## Elemente und Attribute  
 Das `update`\-Element ist erforderlich und befindet sich im `vstav3`\-Namespace.  
  
 Das `update`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`enabled`|Erforderlich.  Aktivieren Sie einen der folgenden Werte:<br /><br /> -   **true**, um nach Aktualisierungen zu suchen.<br />-   **false**, um das Suchen nach Aktualisierungen zu verhindern.|  
  
 Das `update`\-Element verfügt über die folgenden untergeordneten Elemente.  
  
### expiration  
 Das `expiration`\-Element ist erforderlich und befindet sich im `vstav3`\-Namespace.  Dieses Element gibt das Intervall an, in dem die Projektmappe nach Aktualisierungen sucht.  
  
 Das `expiration`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`maximumAge`|-   Erforderlich.  Legen Sie für diesen Wert eine ganze Zahl fest.|  
|`unit`|Erforderlich.  Legen Sie für `unit` einen der folgenden Werte fest:<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## Beispiel für ständiges Suchen nach Aktualisierungen  
  
### Beschreibung  
 Im folgenden Codebeispiel wird ein `update`\-Element veranschaulicht, das so festgelegt ist, dass in Office\-Projektmappen immer nach Aktualisierungen gesucht wird.  
  
### Code  
  
```  
<vstav3:update enabled="true" />  
```  
  
## Beispiel für das Festlegen eines standardmäßigen Aktualisierungsintervalls  
  
### Beschreibung  
 Im folgenden Codebeispiel wird ein `update`\-Element in einem Anwendungsmanifest für Office\-Projektmappen veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels, das Sie im Thema [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md) finden.  
  
### Code  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## Siehe auch  
 [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  