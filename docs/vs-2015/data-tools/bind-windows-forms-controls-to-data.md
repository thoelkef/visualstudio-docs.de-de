---
title: Windows Forms-Steuerelementen an Daten binden | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9b81d3d9f7425874c8a3501d8e1d49eb813b97d9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959311"
---
# <a name="bind-windows-forms-controls-to-data"></a>Binden von Windows Forms-Steuerelementen an Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können Datenquellen an Steuerelemente binden, durch Ziehen von Objekten aus der **Datenquellen** Fenster auf ein Windows-Formular oder auf ein vorhandenes Steuerelement in einem Formular. Bevor Sie Elemente ziehen, können Sie den Typ des Steuerelements festlegen, die, denen Sie binden möchten. Je nachdem, ob Sie in der Tabelle selbst oder eine einzelne Spalte auswählen, werden unterschiedliche Werte angezeigt.  Sie können auch benutzerdefinierte Werte festlegen. Für eine Tabelle bedeutet "Details" an, dass jede Spalte an einem separaten Steuerelement gebunden ist.  
  
 ![Binden Sie die Datenquelle an DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "Raddata Bind-DataSource zu DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Binden Sie an Daten in einem DataGridView-Steuerelement  
 Für DataGridView wird die gesamte Tabelle auf dieses einzelne Steuerelement gebunden. Wenn Sie ein DataGridView-Steuerelement auf das Formular ziehen, wird ein Tool für die Navigation in Datensätzen entfernen (<xref:System.Windows.Forms.BindingNavigator>) wird ebenfalls angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt. In der folgenden Abbildung wird ein TableAdapterManager ebenfalls hinzugefügt, da die Customers-Tabelle eine Beziehung zu der Orders-Tabelle hat. Diese Variablen werden in den automatisch generierten Code als Private Member in der Form-Klasse deklariert. Die automatisch generierten Code für das Ausfüllen der DataGridView befindet sich in den Form_load-Ereignishandler. Der Code zum Speichern der Daten zum Aktualisieren der Datenbank befindet sich in der Save-Ereignishandler für das BindingNavigator. Sie können verschieben oder diesen Code nach Bedarf ändern.  
  
 ![GridView mit BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "Raddata GridView mit BindingNavigator")  
  
 Sie können das Verhalten der DataGridView-Steuerelement und der BindingNavigator anpassen, indem Sie durch Klicken auf das Smarttag, in der oberen rechten Ecke der einzelnen:  
  
 ![DataGridView-Steuerelement und Bindung Navigator Smarttags](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "Raddata DataGridView und Bindung Navigator-Smarttags")  
  
 Wenn die Steuerelemente die Anwendung muss nicht in verfügbar sind die **Datenquellen** Fenster können Sie Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Sie können Elemente auch ziehen die **Datenquellen** auf Steuerelemente, die bereits in einem Formular das Steuerelement an Daten gebunden. Ein Steuerelement, das bereits an Daten gebunden ist, hat seine Daten, die Bindungen auf das Element zuletzt gezogen zurückgesetzt. Um gültige Ablageziele sein, müssen der Steuerelemente zum Anzeigen von der zugrunde liegenden Datentyp des Element gezogene auf ihn von der Lage sein den **Datenquellen** Fenster. Es ist z. B. nicht zulässig, ein Element zu ziehen, die den Datentyp <xref:System.DateTime> auf eine <xref:System.Windows.Forms.CheckBox>, da die <xref:System.Windows.Forms.CheckBox> kann keine Datum anzeigen.  
  
## <a name="bind-to--data-in-individual-controls"></a>Binden Sie an Daten in einzelnen Steuerelementen  
 Wenn Sie auf "Details" eine Datenquelle binden, ist jede Spalte im Dataset an einem separaten Steuerelement gebunden.  
  
 ![Binden Sie die Datenquelle zu Details](../data-tools/media/raddata-bind-data-source-to-details.png "Raddata Bind-DataSource zu Details")  
  
> [!IMPORTANT]
>  Beachten Sie, dass in der vorherigen Abbildung, die Sie aus der Eigenschaft "Orders" in der Customers-Tabelle, nicht aus der Orders-Tabelle ziehen. Durch die Bindung an die Customer.Orders-Eigenschaft, werden vorgenommen, die in der DataGridView Navigationsbefehle sofort in die Detailsteuerelemente. Wenn Sie aus der Tabelle Orders gezogen haben, die Steuerelemente würde weiterhin auf das Dataset gebunden werden, aber nicht würden sie nicht mit dem DataGridView synchronisiert.  
  
 Die folgende Abbildung zeigt die von datengebundenen Steuerelementen, die dem Formular hinzugefügt werden, nachdem die Order-Eigenschaft in der Tabelle Customers, klicken Sie auf "Details gebunden ist" in der **Datenquellen** Fenster.  
  
 ![Tabelle "Orders" gebunden werden, um Details](../data-tools/media/raddata-orders-table-bound-to-details.png "Raddata Orders-Tabelle gebunden, um Details")  
  
 Beachten Sie außerdem, dass für jedes Steuerelement ein Smarttag. Dieses Tag ermöglicht Anpassungen, die auf dieses Steuerelement wird nur angewendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
