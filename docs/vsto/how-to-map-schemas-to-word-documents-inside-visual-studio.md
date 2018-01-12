---
title: 'Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 65ecd3adbeb6f554a901345c2fa5dbf8359a1428
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word wird dargestellten ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden, oder verwenden, oder entwickeln Programme, die unter ausgeführt, im Zusammenhang mit benutzerdefinierten XML-Code von Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn eine Implementierung der einzelnen Funktionen von Microsoft entfernt. Diese Informationen bezüglich Microsoft Word kann nicht gelesen oder von Einzelpersonen oder Organisationen aus, in den Vereinigten Staaten oder die Vertriebsgebiete, denen der verwenden, oder entwickeln Programme, die auf Microsoft Word-Produkte ausgeführt, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält sich nicht wie Produkte, die vor diesem Datum lizenziert oder erworben und lizenziert für die Verwendung außerhalb der Vereinigten Staaten.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Sie können ein XML-Schema zu einem Dokument zuzuordnen, während das Dokument im Visual Studio geöffnet ist. Sie verwenden den gleichen Microsoft Office Word-Tools, die Sie verwenden, wenn das Dokument außerhalb von Visual Studio geöffnet ist. Die Office-Projekt erstellt dieselben Objekte, ob Sie das Schema, das Dokument vor dem zuordnen oder nach der Erstellung der Word-Projektmappe.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Zuordnen ein XML-Schemas zu einem Word-Dokument in Visual Studio  
  
1.  Öffnen Sie das Word-Dokument oder einem Vorlagenprojekt-Projekt, innerhalb von Visual Studio.  
  
2.  Klicken Sie in das Dokument den Fokus auf den Designer.  
  
3.  Klicken Sie im Menüband auf die Registerkarte **Entwickler** .  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  In der **XML** zu gruppieren, klicken Sie auf **Schema**.  
  
     Die **Vorlagen und Add-Ins** Dialogfeld wird geöffnet.  
  
5.  Klicken Sie auf die **XML-Schema** Registerkarte.  
  
6.  Klicken Sie auf **Schema hinzufügen**.  
  
     Die **Schema hinzufügen** Dialogfeld wird geöffnet.  
  
7.  Navigieren Sie zu der Schemadatei, wählen Sie diese, und klicken Sie dann auf **öffnen**.  
  
     Die **Schemaeinstellungen** Dialogfeld wird geöffnet.  
  
8.  Weisen Sie einen Alias ein, oder klicken Sie auf **OK** das Schema ohne Alias hinzufügen.  
  
9. Klicken Sie auf **OK**.  
  
     Die **XML-Struktur** Fenster wird geöffnet.  
  
10. Ziehen Sie Elemente aus der **XML-Struktur** Fenster aus, um den Stellen in Ihrem Dokument, in dem die entsprechenden Steuerelemente erstellt werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML-Schemas und -Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  