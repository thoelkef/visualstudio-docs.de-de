---
title: 'Vorgehensweise: Hinzufügen von globalen Abfragen zu einem TableAdapter | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 681fea494557e555c745d33c07c4e2c25cfe0f88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512383"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Vorgehensweise: Hinzufügen von globalen Abfragen zu einem TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Globale Abfragen* sind SQL-Abfragen, die entweder einen einzelnen (skalaren) Wert oder keinen Wert zurückgeben. Globale Funktionen führen in der Regel Datenbankvorgänge, z. B. einfügungen, Updates, löschungen und das Aggregieren von Informationen, z. B. die Anzahl der Kunden in einer Tabelle oder die Gesamtbetrag der Gebühren für alle Elemente in einer bestimmten Reihenfolge zurückgegeben.  
  
 Hinzufügen von globalen Abfragen durch Ausführen der **Konfigurations-Assistenten für TableAdapter-Abfragen** innerhalb der **Dataset-Designer**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Zum Hinzufügen einer globalen Abfrage zu einem dataset  
  
1.  Öffnen Sie ein Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Ziehen Sie eine **Abfrage** aus der **DataSet** Registerkarte die **Toolbox** auf einen leeren Bereich des der **Dataset-Designer**.  
  
     Die [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md) wird geöffnet.  
  
3.  Wählen Sie eine Verbindung für die Abfrage zu verwenden. Sie können einen aus der Liste auswählen oder erstellen Sie eine neue Verbindung. Wenn Sie eine neue Verbindung erstellen, müssen Sie die Möglichkeit, die sie in der Anwendungskonfigurationsdatei speichern. Weitere Informationen finden Sie unter [Vorgehensweise: Speichern und Bearbeiten von Verbindungszeichenfolgen](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Wählen Sie an, ob SQL-Anweisungen oder gespeicherten Prozeduren verwendet werden soll.  
  
5.  Wählen Sie die gespeicherte Prozedur verwenden oder die **Abfragetyp auswählen** Seite des Assistenten wählen Sie den Typ der Abfrage, die Sie möchten, und klicken Sie dann auf **Weiter**.  
  
6.  Geben Sie eine Abfrage, die die gewünschte Aufgabe, z. B. ausführt `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Durch Ziehen einer Abfrage direkt auf die **Dataset-Designer** erstellt eine Methode, die nur einen Skalarwert (Einzelwert) zurückgibt. Während die Abfrage oder gespeicherte Prozedur, die Sie auswählen, mehr als einen einzelnen Wert zurückgeben kann, gibt die Methode, die vom Assistenten erstellten nur einen einzelnen Wert zurück. Die Abfrage kann z. B. die erste Spalte der ersten Zeile der zurückgegebenen Daten zurückgeben.  
  
7.  Schließen Sie den Assistenten; die Abfrage wird hinzugefügt, um die **Dataset-Designer**. Informationen zum Ausführen der Abfrage finden Sie unter [wie: Ausführen von TableAdapter-Abfragen](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Bearbeiten von typisierten "Datasets"](../data-tools/creating-and-editing-typed-datasets.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Vorgehensweise: Datennavigation mithilfe des BindingNavigator-Steuerelements in Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)