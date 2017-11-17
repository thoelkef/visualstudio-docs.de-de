---
title: Binden von Steuerelementen an Daten in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 9361380aa53b8f6070f4ff9d956620c5344eec7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Binden von Steuerelementen an Daten in Visual Studio
Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Steuerelemente binden. Sie können diese datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf einer Entwurfsoberfläche oder Steuerelemente auf einer Entwurfsoberfläche in Visual Studio.  
  
 In diesem Thema werden die Datenquellen, mit denen Sie datengebundene Steuerelemente erstellen können, beschrieben. Es werden auch einige der allgemeinen Aufgaben beschrieben, die mit der Datenbindung zusammenhängen. Ausführlichere Informationen über das Erstellen von datengebundenen Steuerelementen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) und [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
## <a name="data-sources"></a>Datenquellen  
 Im Kontext der Datenbindung stellt eine Datenquelle die Daten im Arbeitsspeicher, die an eine Benutzeroberfläche gebunden werden kann. Eine Datenquelle kann praktisch sein, eine Entity Framework-Klasse, ein Dataset, einem Dienstendpunkt, der in ein Proxyobjekt .NET, eine LINQ to SQL-Klasse oder beliebiges .NET Objekt oder Auflistung gekapselt wird. Einige Datenquellen ermöglichen es Ihnen, datengebundene Steuerelemente zu erstellen, durch Ziehen von Elementen aus der **Datenquellen** Fenster, während andere Datenquellen nicht der Fall ist. Die folgende Tabelle zeigt, welche Datenquellen unterstützt werden.  
  
|Datenquelle|Drag & Drop-Unterstützung in **Windows Forms-Designer**|Drag & Drop-Unterstützung in **WPF-Designer**|Drag & Drop-Unterstützung in **Silverlight-Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|DataSet|Ja|Ja|Nein|  
|Entity Data Model|Ja<sup>1</sup>|Ja|Ja|  
|LINQ to SQL-Klassen|Nicht<sup>2</sup>|Nicht<sup>2</sup>|Nicht<sup>2</sup>|  
|Dienste (einschließlich [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF-Dienste und Web Services)|Ja|Ja|Ja|  
|Objekt|Ja|Ja|Ja|  
|SharePoint|Ja|Ja|Ja|  
  
 1. Generieren Sie das Modell mit der **Entity Data Model** Assistenten, klicken Sie dann diese Objekte in den Designer ziehen.  
  
 2. LINQ to SQL-Klassen werden nicht angezeigt, der **Datenquellen** Fenster. Sie können jedoch eine neue Objektdatenquelle hinzufügen, die auf LINQ to SQL-Klassen basiert und anschließend diese Objekte in den Designer ziehen, um datengebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O-R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="data-sources-window"></a>Datenquellenfenster  
 Datenquellen stehen dem Projekt als Elemente in der **Datenquellen** Fenster. Dieses Fenster sichtbar ist, oder es wird über die **Ansicht** Menü, wenn eine Form-Entwurfsoberfläche in Ihrem Projekt das aktive Fenster ist. Sie können Elemente auch ziehen, über dieses Fenster, um Steuerelemente zu erstellen, die an den zugrunde liegenden Daten gebunden sind, und Sie können auch die Datenquellen konfigurieren, indem Sie mit der rechten Maustaste.  
  
 ![Datenquellenfenster](../data-tools/media/raddata-data-sources-window.png "Raddata Fenster "Datenquellen"")  
  
 Für jeden Datentyp, der in der **Datenquellen** Fenster, ein Standardsteuerelement wird erstellt, wenn Sie das Element in den Designer ziehen. Vor dem Ziehen eines Elements aus der **Datenquellen** Fenster, ändern Sie das Steuerelement, das erstellt wird. Weitere Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Aufgaben beim Binden von Steuerelementen an Daten  
 Die folgende Tabelle enthält einige der häufigsten Aufgaben, die Sie zum Binden von Steuerelementen an Daten ausführen.  
  
|Aufgabe|Weitere Informationen|  
|----------|----------------------|  
|Öffnen der **Datenquellen** Fenster.|Öffnen Sie im Editor eine Entwurfsoberfläche und wählen Sie **Ansicht** > **Datenquellen**.|  
|Fügen Sie dem Projekt eine Datenquelle hinzu.|[Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)|  
|Legen Sie das Steuerelement, das erstellt wird, wenn Sie ein Element aus ziehen die **Datenquellen** in den Designer.|[Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Ändern Sie die Liste der Steuerelemente, die Elementen in zugeordnet sind die **Datenquellen** Fenster.|[Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Erstellen Sie datengebundene Steuerelemente.|[Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|  
|Binden Sie an ein Objekt oder eine Auflistung.|[Binden von Objekten in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtern von Daten, die in der Benutzeroberfläche angezeigt wird.|[Gewusst wie: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Anpassen von Beschriftungen für Steuerelemente.|[Gewusst wie: Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Windows Forms-Datenbindung](/dotnet/framework/winforms/windows-forms-data-binding)