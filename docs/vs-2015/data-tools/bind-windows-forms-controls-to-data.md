---
title: Binden von Windows Forms-Steuerelementen an Daten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672978"
---
# <a name="bind-windows-forms-controls-to-data"></a>Binden von Windows Forms-Steuerelementen an Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Datenquellen an Steuerelemente binden, indem Sie Objekte aus dem **Datenquellen** Fenster auf ein Windows Form oder auf ein vorhandenes Steuerelement in einem Formular ziehen. Vor dem Ziehen von Elementen können Sie den Steuer Elementtyp festlegen, an den die Bindung erfolgen soll. Abhängig davon, ob Sie die Tabelle selbst oder eine einzelne Spalte auswählen, werden unterschiedliche Werte angezeigt.  Sie können auch benutzerdefinierte Werte festlegen. Für eine Tabelle bedeutet "Details", dass jede Spalte an ein separates Steuerelement gebunden ist.

 ![Datenquelle an DataGridView binden](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata-Datenquelle an DataGridView binden")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Binden an Daten in einem DataGridView-Steuerelement
 Für DataGridView ist die gesamte Tabelle an dieses einzelne Steuerelement gebunden. Wenn Sie ein DataGridView-Steuerelemente auf das Formular ziehen, wird auch eine Tool Leiste zum Navigieren in Datensätzen (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponenten Leiste angezeigt. In der folgenden Abbildung wird auch ein TableAdapterManager hinzugefügt, da die Customers-Tabelle eine Beziehung zur Orders-Tabelle aufweist. Diese Variablen werden alle im automatisch generierten Code als private Member in der Formular Klasse deklariert. Der automatisch generierte Code zum Auffüllen der DataGridView befindet sich im Form_Load-Ereignishandler. Der Code zum Speichern der Daten zum Aktualisieren der Datenbank befindet sich im Speicher Ereignishandler für BindingNavigator. Sie können diesen Code nach Bedarf verschieben oder ändern.

 ![GridView mit BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata-GridView mit BindingNavigator")

 Sie können das Verhalten von DataGridView und BindingNavigator anpassen, indem Sie in der rechten oberen Ecke auf das smarttagtag klicken:

 ![Smarttags DataGridView und Binding Navigator](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView und Bindungs Navigator Smarttags")

 Wenn die von der Anwendung benötigten Steuerelemente im **Datenquellen** Fenster nicht verfügbar sind, können Sie Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellen Fenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Sie können auch Elemente aus dem **Datenquellen** Fenster auf Steuerelemente ziehen, die sich bereits in einem Formular befinden, um das Steuerelement an Daten zu binden. Ein Steuerelement, das bereits an Daten gebunden ist, setzt die Daten Bindungen auf das Element zurück, das zuletzt auf das Element gezogen wurde. Um gültige Drop-Ziele zu sein, müssen Steuerelemente in der Lage sein, den zugrunde liegenden Datentyp des Elements anzuzeigen, das aus dem **Datenquellen** Fenster auf das Element gezogen wird. Beispielsweise ist es nicht zulässig, ein Element mit dem Datentyp <xref:System.DateTime> auf einen <xref:System.Windows.Forms.CheckBox> zu ziehen, da die <xref:System.Windows.Forms.CheckBox> kein Datum anzeigen kann.

## <a name="bind-to--data-in-individual-controls"></a>Binden an Daten in einzelnen Steuerelementen
 Wenn Sie eine Datenquelle an "Details" binden, wird jede Spalte im DataSet an ein separates Steuerelement gebunden.

 ![Datenquelle an Details binden](../data-tools/media/raddata-bind-data-source-to-details.png "Datenquelle für raddata an Details binden")

> [!IMPORTANT]
> Beachten Sie, dass Sie in der vorherigen Abbildung aus der Orders-Eigenschaft der Customers-Tabelle und nicht aus der Orders-Tabelle ziehen. Durch Binden an die Customer. Orders-Eigenschaft werden die in der DataGridView vorgenommenen Navigations Befehle sofort in den Details-Steuerelementen angezeigt. Wenn Sie die Tabelle "Orders" aus der Tabelle "Orders" gezogen haben, sind die Steuerelemente weiterhin an das DataSet gebunden, aber nicht mit der DataGridView synchronisiert.

 Die folgende Abbildung zeigt die standardmäßigen Daten gebundenen Steuerelemente, die dem Formular hinzugefügt werden, nachdem die Orders-Eigenschaft in der Customers-Tabelle im **Datenquellen** Fenster an "Details" gebunden ist.

 ![An Details gebundene Tabelle "Orders"](../data-tools/media/raddata-orders-table-bound-to-details.png "Tabelle "raddata Orders" an Details gebunden")

 Beachten Sie auch, dass jedes Steuerelement über ein Smarttag verfügt. Dieses Tag ermöglicht Anpassungen, die nur für dieses Steuerelement gelten.

## <a name="see-also"></a>Siehe auch
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
