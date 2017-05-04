---
title: "Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual&#160;Studio | Microsoft Docs"
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
  - "Zuordnungen [Office-Entwicklung in Visual Studio], XML-Schemas zu Word-Dokumenten"
  - "Word [Office-Entwicklung in Visual Studio], Zuordnen von XML-Schemas"
  - "XML-Schemas [Office-Entwicklung in Visual Studio], Zuordnen"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual&#160;Studio
  **Wichtig** die Informationen, die in diesem Thema bezüglich Microsoft Word erläutert werden, wird ausschließlich für den Nutzen und die Verwendung von Personen und Organisationen, die außerhalb der USA und ihrer Außengebiete befinden, oder die verwenden, oder entwickeln Programme, die auf ausgeführt werden, Microsoft Word\-Produkte dargestellt, die von Microsoft vor Januar 2010 lizenziert wurden, als Microsoft eine Implementierung der bestimmte Funktionen Beziehung zur benutzerdefinierten XML aus Microsoft Word entfernt wurde.  Diese Informationen bezüglich Microsoft Word dürfen nicht von Personen oder Organisationen in den Vereinigten Staaten oder ihren Außengebieten verwendet werden, die Programme verwenden oder entwickeln, die unter Microsoft Word\-Produkten ausgeführt werden, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden. Diese Produkte verhalten sich nicht wie Produkte, die vor diesem Datum lizenziert oder für die Verwendung außerhalb der Vereinigten Staaten erworben und lizenziert wurden.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Sie können einem Dokument ein XML\-Schema zuordnen, während das Dokument in Visual Studio geöffnet ist.  Dabei verwenden Sie dieselben Microsoft Office Word\-Tools, die Sie verwenden, wenn das Dokument außerhalb von Visual Studio geöffnet ist.  Es spielt keine Rolle, ob Sie das Schema vor oder nach dem Erstellen der Word\-Projektmappe dem Dokument zuordnen. Das Office\-Projekt erstellt in beiden Fällen die gleichen Objekte.  
  
### So ordnen Sie einem Word\-Dokument in Visual Studio ein XML\-Schema zu  
  
1.  Öffnen Sie das Word\-Dokument oder das Vorlagenprojekt in Visual Studio.  
  
2.  Klicken Sie im Dokument, um den Fokus in den Designer zu verschieben.  
  
3.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Klicken Sie in der Gruppe **XML** auf **Schema**.  
  
     Das Dialogfeld **Vorlagen und Add\-Ins** wird geöffnet.  
  
5.  Klicken Sie auf die Registerkarte **XML\-Schema**.  
  
6.  Klicken Sie auf **Schema hinzufügen**.  
  
     Das Dialogfeld **Schema hinzufügen** wird geöffnet.  
  
7.  Wechseln Sie zur Schemadatei, wählen Sie sie aus, und klicken Sie auf **Öffnen**.  
  
     Das Dialogfeld **Schemaeinstellungen** wird angezeigt.  
  
8.  Weisen Sie einen Alias zu, oder klicken Sie auf **OK**, um das Schema ohne einen Alias hinzuzufügen.  
  
9. Klicken Sie auf **OK**.  
  
     Das Fenster **XML\-Struktur** wird geöffnet.  
  
10. Ziehen Sie Elemente aus dem Fenster **XML\-Struktur** an die Positionen in Ihrem Dokument, an denen die entsprechenden Steuerelemente erstellt werden sollen.  
  
## Siehe auch  
 [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML-Schemas und -Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  