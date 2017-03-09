---
title: "Gewusst wie: Erstellen eines XML-Schemas aus einem XML-Dokument | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen eines XML-Schemas aus einem XML-Dokument
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der XML\-Editor ermöglicht Ihnen, ein XSD\-Schema \(XML Schema Definition Language\) aus einem XML\-Dokument zu erstellen.Das XML\-Instanzdokument bestimmt wie folgt, auf welche Weise das Schema generiert wird:  
  
-   Wenn dem XML\-Dokument kein Schema oder keine DTD \(Document Type Definition\) zugeordnet ist, wird mithilfe der Daten im XML\-Dokument ein neues XML\-Schema abgeleitet.  
  
-   Wenn das XML\-Dokument eine zugeordnete DTD enthält, werden die externe DTD und die interne Teilmenge in ein entsprechendes XML\-Schema konvertiert.  
  
-   Wenn das XML\-Dokument ein XDR\-Inlineschema \(XML\-Data Reduced\) enthält, wird das XDR\-Schema in ein entsprechendes XML\-Schema konvertiert.  
  
 Mit den erstellten Schemata wird anschließend IntelliSense für das XML\-Dokument bereitgestellt.  
  
 Weitere Informationen zum Schemarückschlussmodul finden Sie unter [Herleiten eines XML\-Schemas](../Topic/Inferring%20an%20XML%20Schema.md).  
  
### So erstellen Sie ein XML\-Schema  
  
1.  Laden Sie ein XML\-Instanzdokument im XML\-Editor.  
  
2.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Schema erstellen**.  
  
     Ein XML\-Schemadokument wird für jeden im XML\-Instanzdokument gefundenen Namespace erstellt und geöffnet.Jedes Schema wird als sonstige temporäre Datei geöffnet.  
  
     Die Schemas können auf Datenträger gespeichert, dem Projekt hinzugefügt oder verworfen werden.  
  
    > [!NOTE]
    >  Der Befehl **Schema erstellen** ist auch im Kontextmenü des XML\-Editors und im Menü **XML** verfügbar.  
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)