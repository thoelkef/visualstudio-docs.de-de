---
title: Anzeigen verknüpfter Daten in WPF-Anwendungen | Microsoft-Dokumentation
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4068bcbf3ead7114013b93f02a784d682e5b4d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521156"
---
# <a name="display-related-data-in-wpf-applications"></a>Zeigen Sie verknüpfter Daten in WPF-Anwendungen an
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anzeigen verknüpfter Daten in WPF-Anwendungen](https://docs.microsoft.com/visualstudio/data-tools/display-related-data-in-wpf-applications).  
  
  
In einigen Anwendungen empfiehlt es sich zum Arbeiten mit Daten, die stammen aus mehreren Tabellen oder Entitäten, die in einer über-/ unterordnungsbeziehung miteinander verknüpft sind. Beispielsweise möchten Sie ein Raster anzuzeigen, die Kunden aus einem `Customers` Tabelle. Wenn der Benutzer einen bestimmten Kunden auswählt, handelt es sich bei einem anderen Raster zeigt die Aufträge dieses Kunden aus einem verbundenen `Orders` Tabelle.  
  
 Sie können angeben, Erstellen von datengebundenen Steuerelementen, die zugehörigen Daten anzeigen, indem das Ziehen von Elementen aus der **Datenquellen** in den WPF-Designer.  
  
## <a name="to-create-controls-that-display-related-records"></a>So erstellen Sie Steuerelemente, die verknüpfte Datensätze anzeigen  
  
1.  Auf der **Daten** Menü klicken Sie auf **Datenquellen anzeigen** zum Öffnen der **Datenquellen** Fenster.  
  
2.  Klicken Sie auf **neue Datenquelle hinzufügen**, und führen Sie die **Datenquellenkonfiguration** Assistenten.  
  
3.  Öffnen Sie den WPF-Designer, und stellen Sie sicher, dass der Designer ein Container enthält, die ein gültiges Ablageziel für die Elemente in der **Datenquellen** Fenster.  
  
     Weitere Informationen über gültige Ablageziele finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  In der **Datenquellen** Fenster, erweitern Sie den Knoten, die die übergeordnete Tabelle darstellt oder ein Objekt in der Beziehung. Die übergeordnete Tabelle oder das Objekt ist auf der Seite "1" einer 1: n Beziehung.  
  
5.  Ziehen Sie den übergeordneten Knoten (oder einzelne Elemente im übergeordneten Knoten) aus der **Datenquellen** auf ein gültiges Ablageziel im Designer.  
  
     Visual Studio generiert XAML, das neue datengebundene Steuerelemente für jedes Element erstellt, die Sie ziehen. Das XAML fügt auch ein neues <xref:System.Windows.Data.CollectionViewSource> für die übergeordnete Tabelle oder ein Objekt, das die Ressourcen des Ablageziels. Für einige Datenquellen generiert Visual Studio auch Code aus, um die Daten in die übergeordnete Tabelle oder das Objekt laden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  In der **Datenquellen** Fenster Suchen Sie die zugehörige untergeordnete Tabelle oder das Objekt. Verknüpfte untergeordnete Tabellen und Objekte werden als erweiterbare Knoten am unteren Rand des übergeordneten Knotens der Liste der Daten.  
  
7.  Ziehen Sie den untergeordneten Knoten (oder einzelne Elemente in der untergeordnete Knoten) aus der **Datenquellen** auf ein gültiges Ablageziel im Designer.  
  
     Visual Studio generiert XAML, das neue datengebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Das XAML fügt auch ein neues <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder ein Objekt, das die Ressourcen des Ablageziels. Diese neue <xref:System.Windows.Data.CollectionViewSource> an die übergeordnete Tabelle oder ein Objekt, das Sie gerade in den Designer gezogen haben die Eigenschaft gebunden ist. Für einige Datenquellen generiert Visual Studio auch Code aus, um die Daten in die untergeordnete Tabelle oder ein Objekt zu laden.  
  
     Die folgende Abbildung veranschaulicht den dazugehörigen **Bestellungen** Tabelle mit den **Kunden** Tabelle in einem Dataset in der **Datenquellen** Fenster.  
  
     ![Datenquellen-Fenster mit der Beziehung](../data-tools/media/datasources2.gif "DataSources2")  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

