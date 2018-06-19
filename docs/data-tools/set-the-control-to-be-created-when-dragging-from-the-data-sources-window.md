---
title: Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5b1701b95f86f3645ea7d54a47f8b3c7b36b3fd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922335"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll
Sie können datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** Fenster in den WPF- oder Windows Forms-Designer. Jedes Element in der **Datenquellen** verfügt über ein Standardsteuerelement, das erstellt wird, wenn Sie es in den Designer ziehen. Sie können jedoch ein anderes Steuerelement erstellen.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Legen Sie die Steuerelemente, die für Datentabellen oder Objekte erstellt werden
Bevor Sie Elemente ziehen, die die Datentabellen oder Objekte darstellen der **Datenquellen** Fenster können Sie auswählen, um alle Daten in einem Steuerelement anzuzeigen oder um jede Spalte oder Eigenschaft in einem separaten Steuerelement anzuzeigen.

In diesem Kontext ist der Begriff *Objekt* bezieht sich auf ein benutzerdefiniertes Geschäftsobjekt, eine Entität (in einem Entity Data Model) oder ein Objekt, das von einem Dienst zurückgegeben.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>So legen Sie die Steuerelemente fest, die für Datentabellen oder Objekte erstellt werden sollen

1.  Der WPF- oder der Windows Forms-Designer muss geöffnet sein.

2.  In der **Datenquellen** Fenster, wählen Sie das Element, das die Datentabelle darstellt oder ein Objekt festgelegt werden sollen.

3.  Klicken Sie auf das Dropdownmenü für das Element, und klicken Sie im Menü auf eines der folgenden Elemente:

    -   Um jedes Datenfeld in einem separaten Steuerelement anzuzeigen, klicken Sie auf **Details**. Wenn Sie das Datenelement in den Designer ziehen, werden für jede Spalte bzw. jede Eigenschaft der übergeordneten Datentabelle oder des Objekts ein anderes datengebundenes Steuerelement sowie Bezeichnungen für jedes Steuerelement erstellt.

    -   Um alle Daten in einem einzelnen Steuerelement anzuzeigen, wählen Sie ein anderes Steuerelement in der Liste, z. B. **DataGrid** oder **Liste** in einer WPF-Anwendung oder **DataGridView** in einer Windows Forms die Anwendung.

    Die Liste der verfügbaren Steuerelemente hängt vom Designer geöffneten, welche Version von .NET Framework das Projekt abzielt, und gibt an, ob Sie benutzerdefinierte Steuerelemente hinzugefügt haben, unterstützen Datenbindung an die **Toolbox**. Wenn das Steuerelement, das Sie erstellen möchten, nicht in der Liste der verfügbaren Steuerelemente ist, können Sie das Steuerelement zur Liste hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Erfahren Sie, wie ein benutzerdefiniertes Windows Forms-Steuerelement zu erstellen, die die Liste der Steuerelemente für Datentabellen oder Objekte in hinzugefügt werden kann die **Datenquellen** Fenster finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die komplexe Daten unterstützt Binden von](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Legen Sie die Steuerelemente für Datenspalten oder-Eigenschaften erstellt werden
Bevor Sie ein Element zu ziehen, der eine Spalte oder eine Eigenschaft eines Objekts aus der **Datenquellen** Fenster in den Designer, Sie können die zu erstellende Steuerelement festlegen.

#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>So legen Sie die Steuerelemente fest, die für Spalten oder Eigenschaften erstellt werden sollen

1.  Der WPF- oder der Windows Forms-Designer muss geöffnet sein.

2.  In der **Datenquellen** Fenster, erweitern Sie die gewünschte Tabelle oder Objekt, sodass die Spalten bzw. Eigenschaften angezeigt.

3.  Wählen Sie jede Spalte oder jede Eigenschaft aus, für die das Steuerelement erstellt werden soll.

4.  Klicken Sie auf das Dropdownmenü für die Spalte oder die Eigenschaft, und wählen Sie das Steuerelement aus, das beim Ziehen des Elements in den Designer erstellt werden soll.

     Die Liste der verfügbaren Steuerelemente hängt vom Designer geöffneten, welche Version von .NET Framework das Projekt abzielt, und welche benutzerdefinierten Steuerelemente, die Sie Binden von Daten hinzugefügt haben unterstützen die **Toolbox**. Wenn das gewünschte Steuerelement in der Liste der verfügbaren Steuerelemente aufgeführt ist, können Sie der Liste das Steuerelement hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Erfahren Sie, wie ein benutzerdefiniertes Steuerelement zu erstellen, die die Liste der Steuerelemente für Datenspalten oder-Eigenschaften in hinzugefügt werden, können, die **Datenquellen** Fenster finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindungunterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Wenn Sie ein Steuerelement für die Spalte oder Eigenschaft erstellen möchten, wählen Sie **keine** im Dropdown-Menü. Dies ist nützlich, wenn Sie die übergeordnete Tabelle oder das Objekt in den Designer ziehen, aber die Spalte oder die Eigenschaft nicht einschließen möchten.

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)