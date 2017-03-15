---
title: "Bitmapelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, Bitmaps"
  - "Bitmaps-Element (VSCT-XML-Schema)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Bitmapelement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert eine Bitmap. Die Bitmap wird von einer Ressource oder aus einer Datei geladen.  
  
## Syntax  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die GUID der GUID\-ID\-Befehls\-ID.<br /><br /> Das Guid\-Attribut für eine Bitmap ist nicht mit jedem VSPackage oder anderen Befehlsgruppe verknüpft.  Sie sollten für die bitmapdefinition eindeutig sein und sollte nicht für andere Zwecke verwendet werden.|  
|resID|ID der GUID\-ID\-Befehls\-ID. Die ResID oder das Href\-Attribut ist erforderlich.<br /><br /> Die ResID\-Attribut ist ein Integer\-Ressourcen\-ID, die die Bitmap Streifen bestimmt, der während der Befehlstabelle Zusammenführen geladen werden soll.  Wenn die Befehlstabelle geladen wird, werden die Bitmaps angegeben, indem die Ressourcen\-ID aus der Ressource des gleichen Moduls geladen.|  
|"usedlist"|Erforderlich, wenn das Attribut ResID vorhanden ist. Wählt die verfügbaren Images in der Bitmap Streifen.|  
|href|Der Pfad für die Bitmap. Die ResID oder das Href\-Attribut ist erforderlich.<br /><br /> Die Include\-Pfad wird für die angegebene Bilddatei, durchsucht, die in der resultierenden Binärdatei eingebettet ist.  Während der Befehl Tabelle verbinden wird das Bild kopiert, und ist keine zusätzliche Ressourcensuche oder Laden erforderlich.  Wenn das Attribut "usedlist" nicht vorhanden ist, sind alle Abbilder in die Bereichsstreifen verfügbar. **Note:**  Bilder können in verschiedenen Formaten angegeben werden, die BMP\-, PNG\- und GIF enthalten.  Frühere Versionen des Compilers unterstützten nicht Bitmaps mit 32\-Bit, die Alphainformationen für teilweise Transparenz. Die problemumgehung für diese Versionen ist das PNG\-Format verwenden.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Bitmaps\-Element](../extensibility/bitmaps-element.md)|Gruppen\-Bitmap\-Elemente.|  
  
## Beispiel  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)