---
title: Binden von Steuerelementen an Daten
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
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d0e34075fbadcc998dba09d1b7c13a5ffacc606
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556874"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Binden von Steuerelementen an Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Steuerelemente binden. Sie können diese datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** Fenster auf einer Entwurfsoberfläche oder Steuerelemente auf einer Oberfläche in Visual Studio.

 In diesem Thema werden die Datenquellen, mit denen Sie datengebundene Steuerelemente erstellen können, beschrieben. Es werden auch einige der allgemeinen Aufgaben beschrieben, die mit der Datenbindung zusammenhängen. Ausführlichere Informationen dazu, wie Sie datengebundene Steuerelemente erstellen, finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) und [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Datenquellen
 Im Kontext der Datenbindung stellt eine Datenquelle die Daten im Arbeitsspeicher, die in die Benutzeroberfläche gebunden werden kann. Eine Datenquelle kann praktisch sein, eine Entity Framework-Klasse, ein Dataset, einen Dienstendpunkt, der in ein Proxyobjekt .NET, eine LINQ to SQL-Klasse, oder jedes beliebige Objekt .NET oder Auflistung gekapselt wird. Einige Datenquellen ermöglichen es Ihnen, datengebundene Steuerelemente durch Ziehen von Elementen aus dem Fenster **Datenquellen** zu erstellen. Bei anderen Datenquellen ist dies hingegen nicht der Fall. Die folgende Tabelle zeigt, welche Datenquellen unterstützt werden.

|Datenquelle|Drag & Drop-Unterstützung im **Windows Forms-Designer**|Drag & Drop-Unterstützung im **WPF-Designer**|Drag & Drop-Unterstützung im **Silverlight-Designer**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|DataSet|Ja|Ja|Nein|
|Entity Data Model|Ja<sup>1</sup>|Ja|Ja|
|LINQ to SQL-Klassen|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|
|Dienste (einschließlich [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF-Dienste und Webdienste)|Ja|Ja|Ja|
|Object|Ja|Ja|Ja|
|SharePoint|Ja|Ja|Ja|

 1. Generieren Sie das Modell, indem die **Entity Data Model** -Assistenten klicken Sie dann die Objekte in den Designer ziehen.

 2. LINQ to SQL-Klassen werden nicht im Fenster **Datenquellen** angezeigt. Sie können jedoch eine neue Objektdatenquelle hinzufügen, die auf LINQ to SQL-Klassen basiert und anschließend diese Objekte in den Designer ziehen, um datengebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>Datenquellenfenster
 Datenquellen stehen dem Projekt als Elemente im Fenster **Datenquellen** zur Verfügung. Dieses Fenster sichtbar ist, oder es wird über die **Ansicht** Menü, wenn eine Formular-Entwurfsoberfläche in Ihrem Projekt das aktive Fenster ist. Sie können Elemente ziehen, in diesem Fenster aus, um Steuerelemente zu erstellen, die den zugrunde liegenden Daten gebunden sind, und Sie können auch die Datenquellen konfigurieren, indem Sie mit der rechten Maustaste.

 ![Datenquellenfenster](../data-tools/media/raddata-data-sources-window.png "Raddata Fenster \"Datenquellen\"")

 Für jeden Datentyp, der im Fenster **Datenquellen** angezeigt wird, wird ein standardmäßiges Steuerelement erstellt, wenn das Element in den Designer gezogen wird. Bevor Sie ein Element aus ziehen die **Datenquellen** Fenster ändern Sie das Steuerelement, das erstellt wird. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Aufgaben beim Binden von Steuerelementen an Daten
 Die folgende Tabelle enthält einige der am häufigsten auszuführenden Aufgaben Sie ausführen, um die Steuerelemente an Daten binden.

|Aufgabe|Weitere Informationen|
|----------|----------------------|
|Öffnen Sie das Fenster **Datenquellen**.|Öffnen Sie im Editor eine Entwurfsoberfläche und wählen Sie **Ansicht** > **Datenquellen**.|
|Fügen Sie dem Projekt eine Datenquelle hinzu.|[Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)|
|Legen Sie das Steuerelement fest, das erstellt wird, wenn Sie ein Element vom Fenster **Datenquellen** in den Designer ziehen.|[Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Ändern Sie die Liste der Steuerelemente, die Elementen im Fenster **Datenquellen** zugeordnet sind.|[Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Erstellen Sie datengebundene Steuerelemente.|[Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Binden Sie an ein Objekt oder eine Auflistung.|[Binden von Objekten in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtern von Daten, die in der Benutzeroberfläche angezeigt wird.|[Gewusst wie: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Anpassen von Beschriftungen für Steuerelemente.|[Gewusst wie: Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms-Datenbindung](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
