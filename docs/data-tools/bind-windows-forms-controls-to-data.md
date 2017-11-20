---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
Title: "Binden von Windows Forms-Steuerelementen an Daten | Microsoft Docs"ms.custom:" "ms.date:" 11/04/2016"ms.reviewer:" "ms.suite:" "ms. tgt_pltfrm:" "ms.topic:"Artikel"Helpviewer_keywords: 
  - "zum Anzeigen von Daten Steuerelemente von Windows Forms"
  - "Windows Forms, Anzeigen von Daten"
  - "Data Sources, anzeigen"
  - "Daten [Windows Forms], Anzeigen von" ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 Autor: "Gewarren" ms.author: "Gewarren"-Manager: Ghogen ms.technology: "Vs-Daten-Tools"
---
# <a name="bind-windows-forms-controls-to-data"></a>Binden Sie Windows Forms-Steuerelementen an Daten.
Sie können Datenquellen an Steuerelemente binden, durch Ziehen der Objekte aus der **Datenquellen** Fenster auf einem Windows Form oder auf ein vorhandenes Steuerelement in einem Formular. Bevor Sie Elemente ziehen, können Sie den Typ des Steuerelements festlegen, denen Sie binden möchten. Je nachdem, ob Sie der Tabelle selbst oder eine einzelne Spalte auswählen, werden unterschiedliche Werte angezeigt.  Sie können auch benutzerdefinierte Werte festlegen. Für eine Tabelle bedeutet "Details" an, dass jede Spalte an einem separaten Steuerelement gebunden ist.  

![Binden Sie die Datenquelle an DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "Raddata Bind-DataSource zu DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Binden Sie an Daten in einem DataGridView-Steuerelement  
Für DataGridView wird die gesamte Tabelle auf das entsprechende einzelne Steuerelement gebunden. Wenn Sie ein DataGridView-Steuerelement in das Formular ziehen, wird ein Tool für die Navigation in den Datensätzen Bereichsstreifens (<xref:System.Windows.Forms.BindingNavigator>) wird ebenfalls angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt. In der folgenden Abbildung ist ein TableAdapterManager auch hinzugefügt, da die Customers-Tabelle eine Beziehung zu der Tabelle Orders sind. Diese Variablen werden in den automatisch generierten Code als Private Member in der Form-Klasse deklariert. Die automatisch generierten Code zum Ausfüllen der DataGridView befindet sich im Form_load-Ereignishandler. Der Code zum Speichern der Daten zum Aktualisieren der Datenbank befindet sich im Ereignishandler speichern für das BindingNavigator. Sie können verschieben oder ändern diesen Code nach Bedarf.  
  
 ![GridView mit BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "Raddata GridView mit BindingNavigator")  
  
 Sie können das Verhalten der DataGridView-Steuerelement und der BindingNavigator anpassen, indem Sie durch Klicken auf das Smarttag in der oberen rechten Ecke der einzelnen:  
  
 ![DataGridView-Steuerelement und Binden von Navigator Smarttags](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "Raddata DataGridView und Binden von Navigator-Smarttags")  
  
 Wenn die Steuerelemente die Anwendung muss nicht verfügbar sind die **Datenquellen** Fenster können Sie Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Sie können auch ziehen Sie Elemente aus der **Datenquellen** auf Steuerelemente, die bereits in einem Formular das Steuerelement an Daten gebunden. Ein Steuerelement, das bereits an Daten gebunden ist, hat seine Daten auf das Element zuletzt gezogen Bindungen zurückgesetzt. Um gültige Ablageziele sein, Steuerelemente zum Anzeigen von dem zugrunde liegenden Datentyp, von der auf diesem aus gezogene Element in der Lage sein müssen die **Datenquellen** Fenster. Es ist z. B. nicht zulässig, ein Element zu ziehen, die einen-Datentyp zugehört <xref:System.DateTime> auf eine <xref:System.Windows.Forms.CheckBox>, da die <xref:System.Windows.Forms.CheckBox> kann keine Datum anzeigen.  
  
## <a name="bind-to--data-in-individual-controls"></a>Binden Sie an Daten in einzelnen Steuerelementen  
 Wenn Sie auf "Details" eine Datenquelle binden, wird jede Spalte im Dataset auf einem separaten Steuerelement gebunden.  
  
 ![Binden Sie die Datenquelle zu Details](../data-tools/media/raddata-bind-data-source-to-details.png "Raddata Bind-DataSource zu Details")  
  
> [!IMPORTANT]
>  Beachten Sie, dass in der obigen Abbildung können Sie aus der Orders-Eigenschaft der Customers-Tabelle nicht aus der Orders-Tabelle ziehen. Von der Bindung der Customer.Orders-Eigenschaft, sind Navigationsbefehle vorgenommen werden, in der DataGridView sofort in die Steuerelemente für Details dargestellt. Wenn Sie aus der Tabelle Orders gezogen haben, die Steuerelemente würde weiterhin auf das Dataset gebunden werden, aber nicht würden sie nicht mit der DataGridView synchronisiert.  
  
 Die folgende Abbildung zeigt die Standardeinstellung von datengebundenen Steuerelementen, die dem Formular hinzugefügt werden, nachdem die Orders-Eigenschaft in der Tabelle Customers, auf "Details gebunden ist" in der **Datenquellen** Fenster.  
  
 ![Tabelle "Orders" gebunden werden, um Details](../data-tools/media/raddata-orders-table-bound-to-details.png "Tabelle "Orders" Raddata gebunden werden, um Details")  
  
 Beachten Sie außerdem, dass jedes Steuerelement ein Smarttag verfügt. Dieses Tag kann Anpassungen, die auf das entsprechende Steuerelement nur gelten.  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)