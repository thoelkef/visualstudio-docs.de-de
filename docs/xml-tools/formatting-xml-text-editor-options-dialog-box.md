---
title: "Formatierung, XML, Texteditor, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Formatierung, XML, Texteditor, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die Formatierungseinstellungen für den XML\-Editor angeben.Sie können vom Menü **Extras** aus auf das Dialogfeld **Optionen** zugreifen.  
  
> [!NOTE]
>  Diese Einstellungen sind verfügbar, wenn Sie den Ordner **Texteditor**, dann den **XML**\-Ordner und anschließend im Dialogfeld **Optionen** die Option **Formatierung** auswählen.  
  
## Attribute  
 **Manuelle Attributformatierung beibehalten**  
 Attribute werden nicht neu formatiert.Dies ist der Standardwert.  
  
> [!NOTE]
>  Wenn sich die Attribute auf mehreren Zeilen befinden, zieht der Editor jede Attributzeile ein, sodass das Einzugsmuster des übergeordneten Elements festgelegt wird.  
  
 **Attribute jeweils in einer eigenen Zeile ausrichten**  
 Richtet das zweite und die nachfolgenden Attribute vertikal aus, damit sie dem Einzug des ersten Attributs entsprechen.Der folgende XML\-Text veranschaulicht, wie die Attribute ausgerichtet werden.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## Automatisch neu formatieren  
 **Bei Einfügen aus der Zwischenablage**  
 Formatiert den aus der Zwischenablage eingefügten XML\-Text neu.  
  
 **Bei Komplettierung des Endtags**  
 Formatiert das Element neu, wenn das Endtag vervollständigt wird.  
  
## Gemischter Inhalt  
 **Gemischten Inhalt standardmäßig beibehalten**  
 Bestimmt, ob der Editor gemischten Inhalt neu formatiert.Der Editor versucht standardmäßig, gemischten Inhalt neu zu formatieren, es sei denn, der Inhalt befindet sich in einem `xml:space="preserve"`\-Gültigkeitsbereich.  
  
 Wenn ein Element eine Mischung aus Text und Markup enthält, wird der Inhalt als gemischter Inhalt betrachtet.Es folgt als Beispiel ein Element mit gemischtem Inhalt.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## Siehe auch  
 [XML\-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)   
 [Komponenten des XML\-Editors](../xml-tools/xml-editor-components.md)