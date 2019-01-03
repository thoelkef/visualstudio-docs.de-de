---
title: 'Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: fcd9d63b691096f0ace035e1e8384f904578f411
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867825"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word festgelegt ist, ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden oder mit, dargestellten oder entwickeln Programme, auf denen ausgeführt wird, im Zusammenhang mit benutzerdefinierten XML-Code aus Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn Microsoft eine Implementierung von bestimmten Funktionen entfernt. Diese Informationen in Bezug auf Microsoft Word kann nicht gelesen oder durch Einzelpersonen oder Organisationen, die in den Vereinigten Staaten oder der Gebiete, die mithilfe von, oder Entwickeln von Anwendungen, die Microsoft Word-Produkte ausgeführt werden, die von Microsoft, nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält nicht als Produkte, die vor diesem Datum lizenziert oder erworben und für die Verwendung außerhalb der USA lizenziert.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Sie können ein XML-Schema in ein Dokument zuordnen, während das Dokument in Visual Studio geöffnet ist. Sie verwenden den gleichen Microsoft Office Word-Tools, die Sie verwenden, wenn das Dokument außerhalb von Visual Studio geöffnet ist. Das Office-Projekt erstellt die gleichen Objekte, ob Sie das Schema, das Dokument vor dem zuordnen oder nach der Erstellung der Word-Projektmappe.  
  
## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Ordnen Sie eine XML-Schema in ein Word-Dokument in Visual Studio  
  
1.  Öffnen Sie das Word-Dokument oder einer Vorlage-Projekt, in Visual Studio.  
  
2.  Klicken Sie auf das Dokument, das den Fokus auf den Designer.  
  
3.  Klicken Sie auf dem Menüband auf die **Developer** Registerkarte.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  In der **XML** auf **Schema**.  
  
     Die **Vorlagen und Add-Ins** Dialogfeld wird geöffnet.  
  
5.  Klicken Sie auf die **XML-Schema** Registerkarte.  
  
6.  Klicken Sie auf **Schema hinzufügen**.  
  
     Die **Schema hinzufügen** Dialogfeld wird geöffnet.  
  
7.  Navigieren Sie zu der Schemadatei, wählen Sie ihn, und klicken Sie dann auf **öffnen**.  
  
     Die **Schema Einstellungen** Dialogfeld wird geöffnet.  
  
8.  Weisen Sie einen Alias, oder klicken Sie auf **OK** das Schema ohne Alias hinzufügen.  
  
9. Klicken Sie auf **OK**.  
  
     Die **XML-Struktur** Fenster wird geöffnet.  
  
10. Ziehen Sie Elemente aus der **XML-Struktur** Fenster aus, um den Stellen in Ihrem Dokument, in denen die entsprechenden Steuerelemente erstellt werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML-Schemas und Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
