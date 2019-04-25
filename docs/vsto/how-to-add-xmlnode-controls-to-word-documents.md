---
title: 'Vorgehensweise: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79ae6aee44f720b868e30c831ee4d6aa61c9611d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090406"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Vorgehensweise: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word festgelegt ist, ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden oder mit, dargestellten oder entwickeln Programme, auf denen ausgeführt wird, im Zusammenhang mit benutzerdefinierten XML-Code aus Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn Microsoft eine Implementierung von bestimmten Funktionen entfernt. Diese Informationen in Bezug auf Microsoft Word kann nicht gelesen oder durch Einzelpersonen oder Organisationen, die in den Vereinigten Staaten oder der Gebiete, die mithilfe von, oder Entwickeln von Anwendungen, die Microsoft Word-Produkte ausgeführt werden, die von Microsoft, nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält nicht als Produkte, die vor diesem Datum lizenziert oder erworben und für die Verwendung außerhalb der USA lizenziert.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Wenn Sie Microsoft Office Word-Dokument ein nicht wiederholtes XML-Schemaelement zuordnen, fügt Visual Studio automatisch eine <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement zum Dokument. Weitere Informationen zum Zuordnen von sich wiederholenden XML-Schemaelemente, finden Sie unter [Vorgehensweise: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
>  Die <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement ist nicht verfügbar ist, aus der **Toolbox** oder **Datenquellen** Fenster, und es kann nicht programmgesteuert erstellt werden.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Hinzufügen von XMLNode-Steuerelement zu einem Dokument

1. Klicken Sie in das Dokument in Visual Studio-Designer, auf dem Menüband auf die **Developer** Registerkarte.

    > [!NOTE]
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. In der **XML** auf **Schema**.

     Die **Vorlagen und Add-Ins** Dialogfeld wird geöffnet.

3. Klicken Sie auf die **XML-Schema** Registerkarte.

4. Klicken Sie auf **Schema hinzufügen**.

     Die **Schema hinzufügen** Dialogfeld wird geöffnet.

5. Wählen Sie ein XML-Schema, das nicht wiederholte Schemaelemente enthält die **Schema hinzufügen** Dialogfeld und klicken Sie auf **öffnen**.

     Die **Schema Einstellungen** Dialogfeld wird angezeigt.

6. Weisen Sie einen Alias, oder klicken Sie auf **OK** das Schema ohne Alias hinzufügen.

     Das Schema wird hinzugefügt, um die **Schema hinzufügen** Dialogfeld.

7. In der **Schema hinzufügen** Dialogfeld klicken Sie auf **OK**.

8. Die **XML-Struktur** Aufgabe wird geöffnet.

9. Klicken Sie auf die sich nicht wiederholendes Schemaelement auf die **XML-Struktur** Aufgabenbereich, um es dem Dokument hinzuzufügen.

     Ein <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement erstellt und dem Projekt hinzugefügt.

## <a name="see-also"></a>Siehe auch
- [XMLNode-Steuerelement](../vsto/xmlnode-control.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
