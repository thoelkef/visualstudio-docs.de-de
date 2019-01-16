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
ms.workload:
- data-storage
ms.openlocfilehash: 0ef06a84fb903b79a40087ac7e7ac98c6964d285
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879996"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll

Sie können datengebundene Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** in den WPF- oder den Windows Forms-Designer ziehen. Jedes Element im Fenster **Datenquellen** verfügt über ein Standardsteuerelement, das erstellt wird, wenn Sie es in den Designer ziehen. Sie können jedoch ein anderes Steuerelement erstellen.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Festlegen der Steuerelemente, die für Datentabellen oder Objekte erstellt werden sollen

Bevor Sie Elemente aus dem Fenster **Datenquellen** ziehen, die Datentabellen oder Objekte darstellen, können Sie zwischen zwei Optionen wählen: Alle Daten können in einem Steuerelement oder jede Spalte bzw. Eigenschaft in einem separaten Steuerelement angezeigt werden.

In diesem Kontext bezieht sich der Begriff *Objekt* auf ein benutzerdefiniertes Geschäftsobjekt, eine Entität (in einem Entity Data Model) oder ein von einem Dienst zurückgegebenes Objekt.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>So legen Sie die Steuerelemente fest, die für Datentabellen oder Objekte erstellt werden sollen

1. Achten Sie darauf die **WPF** Designer oder dem **Windows Forms** -Designer geöffnet ist.

2. Wählen Sie im Fenster **Datenquellen** das Element aus, das die festzulegende Datentabelle oder das Objekt darstellt.

   > [!TIP]
   > Wenn die **Datenquellen** nicht geöffnet ist, können Sie es öffnen, indem Sie auswählen **Ansicht** > **Other Windows** > **Datenquellen**.

3. Klicken Sie auf das Dropdownmenü für das Element, und klicken Sie im Menü auf eines der folgenden Elemente:

    - Klicken Sie auf **Details**, um jedes Datenfeld in einem separaten Steuerelement anzuzeigen. Wenn Sie das Datenelement in den Designer ziehen, werden für jede Spalte bzw. jede Eigenschaft der übergeordneten Datentabelle oder des Objekts ein anderes datengebundenes Steuerelement sowie Bezeichnungen für jedes Steuerelement erstellt.

    - Wählen Sie ein anderes Steuerelement in der Liste, z.B. **DataGrid** oder **List** in einer WPF-Anwendung, oder **DataGridView** in einer Windows Forms-Anwendung aus, um alle Daten in einem einzelnen Steuerelement anzuzeigen.

    Die Liste der verfügbaren Steuerelemente hängt vom geöffneten Designer, der Version von .NET Framework, auf die das Projekt abzielt, und davon ab, ob Sie benutzerdefinierte Steuerelemente hinzugefügt haben, die die Datenbindung zur **Toolbox** unterstützen. Wenn das Steuerelement, die, das Sie erstellen möchten, nicht in der Liste der verfügbaren Steuerelemente ist, können Sie das Steuerelement zur Liste hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Erfahren Sie, wie ein benutzerdefiniertes Windows Forms-Steuerelement zu erstellen, die die Liste der Steuerelemente für Datentabellen oder Objekte im hinzugefügt werden, können, die **Datenquellen** Fenster finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die komplexe Daten unterstützt Binden von](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Legen Sie die Steuerelemente für Datenspalten oder-Eigenschaften erstellt werden soll

Bevor Sie ein Element, das eine Spalte oder eine Eigenschaft eines Objekts im Fenster **Datenquellen** darstellt, in den Designer ziehen, können Sie das zu erstellende Steuerelement festlegen.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>So legen Sie die Steuerelemente fest, die für Spalten oder Eigenschaften erstellt werden sollen

1. Achten Sie darauf die **WPF** Designer oder dem **Windows Forms** -Designer geöffnet ist.

2. Erweitern Sie im Fenster **Datenquellen** die gewünschte Tabelle oder das gewünschte Objekt, sodass die Spalten bzw. Eigenschaften angezeigt werden.

3. Wählen Sie jede Spalte oder jede Eigenschaft aus, für die das Steuerelement erstellt werden soll.

4. Klicken Sie auf das Dropdownmenü für die Spalte oder die Eigenschaft, und wählen Sie das Steuerelement aus, das beim Ziehen des Elements in den Designer erstellt werden soll.

     Die Liste der verfügbaren Steuerelemente hängt vom geöffneten Designer, der Version von .NET Framework, auf die das Projekt abzielt, und davon ab, welche benutzerdefinierten, die Datenbindung zur **Toolbox** unterstützenden Steuerelemente Sie hinzugefügt haben. Wenn das gewünschte Steuerelement in der Liste der verfügbaren Steuerelemente aufgeführt ist, können Sie der Liste das Steuerelement hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Erfahren Sie, wie ein benutzerdefiniertes Steuerelement erstellen, die die Liste der Steuerelemente für Datenspalten oder Eigenschaften im hinzugefügt werden, können, die **Datenquellen** Fenster finden Sie unter [Erstellen eines Windows Forms-Benutzersteuerelements, die einfache Datenbindungunterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Wenn Sie ein Steuerelement für die Spalte oder Eigenschaft erstellen möchten, wählen Sie **keine** im Dropdown-Menü. Dies ist nützlich, wenn Sie die übergeordnete Tabelle oder das Objekt in den Designer ziehen, aber die Spalte oder die Eigenschaft nicht einschließen möchten.

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)