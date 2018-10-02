---
title: Binden von Steuerelementen an Daten in Visual Studio | Microsoft-Dokumentation
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
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85bfcb03ea2f383d8f1517d17c866c2320891aaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516358"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Binden von Steuerelementen an Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
  
Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Steuerelemente binden. Sie können diese datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** Fenster auf einer Entwurfsoberfläche oder Steuerelemente auf einer Oberfläche in Visual Studio.  
  
 In diesem Thema werden die Datenquellen, mit denen Sie datengebundene Steuerelemente erstellen können, beschrieben. Es werden auch einige der allgemeinen Aufgaben beschrieben, die mit der Datenbindung zusammenhängen. Ausführlichere Informationen dazu, wie Sie datengebundene Steuerelemente erstellen, finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) und [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
## <a name="data-sources"></a>Datenquellen  
 Im Kontext der Datenbindung stellt eine Datenquelle die Daten im Arbeitsspeicher, die in die Benutzeroberfläche gebunden werden kann. Eine Datenquelle kann praktisch sein, eine Entity Framework-Klasse, ein Dataset, einen Dienstendpunkt, der in ein Proxyobjekt .NET, eine LINQ to SQL-Klasse, oder jedes beliebige Objekt .NET oder Auflistung gekapselt wird. Einige Datenquellen ermöglichen Ihnen die Erstellung von datengebundenen Steuerelementen durch Ziehen von Elementen aus der **Datenquellen** Fenster, während die Daten aus anderen Quellen nicht der Fall ist. Die folgende Tabelle zeigt, welche Datenquellen unterstützt werden.  
  
|Datenquelle|Drag & Drop-Unterstützung in **der Windows Forms-Designer**|Drag & Drop-Unterstützung in **WPF-Designer**|Drag & Drop-Unterstützung in **Silverlight-Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|DataSet|Ja|Ja|Nein|  
|Entity Data Model|Ja<sup>1</sup>|Ja|Ja|  
|LINQ to SQL-Klassen|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|  
|Dienste (einschließlich [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF-Dienste und Web Services)|Ja|Ja|Ja|  
|Object|Ja|Ja|Ja|  
|SharePoint|Ja|Ja|Ja|  
  
 1. Generieren Sie das Modell, indem die **Entity Data Model** -Assistenten klicken Sie dann die Objekte in den Designer ziehen.  
  
 2. LINQ to SQL-Klassen werden nicht angezeigt, der **Datenquellen** Fenster. Sie können jedoch eine neue Objektdatenquelle hinzufügen, die auf LINQ to SQL-Klassen basiert und anschließend diese Objekte in den Designer ziehen, um datengebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="data-sources-window"></a>Datenquellenfenster  
 Datenquellen für Ihr Projekt verfügbar sind, als Elemente in der **Datenquellen** Fenster. Dieses Fenster sichtbar ist, oder es wird über die **Ansicht** Menü, wenn eine Formular-Entwurfsoberfläche in Ihrem Projekt das aktive Fenster ist. Sie können Elemente ziehen, in diesem Fenster aus, um Steuerelemente zu erstellen, die den zugrunde liegenden Daten gebunden sind, und Sie können auch die Datenquellen konfigurieren, indem Sie mit der rechten Maustaste.  
  
 ![Datenquellenfenster](../data-tools/media/raddata-data-sources-window.png "Raddata Fenster \"Datenquellen\"")  
  
 Für jeden Datentyp, der in erscheint die **Datenquellen** Fenster ein standardmäßiges Steuerelement erstellt, wenn Sie das Element in den Designer ziehen. Bevor Sie ein Element aus ziehen die **Datenquellen** Fenster ändern Sie das Steuerelement, das erstellt wird. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Aufgaben beim Binden von Steuerelementen an Daten  
 Die folgende Tabelle enthält einige der am häufigsten auszuführenden Aufgaben Sie ausführen, um die Steuerelemente an Daten binden.  
  
|Aufgabe|Weitere Informationen|  
|----------|----------------------|  
|Öffnen der **Datenquellen** Fenster.|Öffnen Sie im Editor eine Entwurfsoberfläche und wählen Sie **Ansicht** > **Datenquellen**.|  
|Fügen Sie Ihrem Projekt eine Datenquelle hinzu.|[Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)|  
|Legen Sie das Steuerelement, das erstellt wird, wenn Sie ein Element aus ziehen die **Datenquellen** in den Designer.|[Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Ändern Sie die Liste der Steuerelemente, die mit Elementen verknüpft sind die **Datenquellen** Fenster.|[Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Erstellen Sie datengebundene Steuerelemente.|[Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|  
|Binden Sie an ein Objekt oder eine Auflistung.|[Binden von Objekten in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtern von Daten, die in der Benutzeroberfläche angezeigt wird.|[Gewusst wie: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Anpassen von Beschriftungen für Steuerelemente.|[Gewusst wie: Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Windows Forms-Datenbindung](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)

