---
title: 'Vorgehensweise: Anzeigen von verknüpften Daten in einer Windows Forms-Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3fd7a29e1de66a5b5fd57dab1adbcf99128001ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215461"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können verknüpfte Daten anzeigen, durch Ziehen von Elementen, die gemeinsam die demselben Haupttabellenknoten befinden, aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf das Formular. Beispielsweise verfügt, wenn Sie eine Datenquelle verfügen über eine `Customers` Tabelle und einem verbundenen `Orders` Tabelle sehen Sie beide Tabellen als Knoten der obersten Ebene (in der Strukturansicht) in der **Datenquellen** Fenster. Erweitern Sie den Knoten `Customers`, sodass die Spalten angezeigt werden. Sie sehen, dass es sich bei der letzen Spalte in der Liste um einen erweiterbaren Knoten handelt, der die Tabelle `Orders` darstellt. Dieser Knoten entspricht den verknüpften Bestellungen eines Kunden. Dies bedeutet, dass Sie die anzuzeigenden Elemente bei der Erstellung eines Formulars, das Ihnen die Auswahl eines Kunden und das anschließende Anzeigen einer Liste mit Bestellungen für diesen Kunden erlaubt, aus dieser einzelnen Hierarchie ziehen würden.  
  
 ![Datenquellen-Fenster mit der Beziehung](../data-tools/media/datasources2.gif "DataSources2")  
Erstellen von datengebundenen Steuerelementen, die verknüpfte Datensätze anzeigen  
  
 ![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo") eine Videoversion dieses Themas finden Sie unter [Gewusst I: Update Related Tables](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>So erstellen Sie Steuerelemente, die verknüpfte Datensätze anzeigen  
  
1.  Öffnen Sie das Formular in der [Windows Forms-Designer](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Öffnen der **Datenquellen** Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen des Datenquellenfensters](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Erweitern Sie den Knoten, der die übergeordnete Tabelle in der Beziehung darstellt. (Die übergeordnete Tabelle ist die Tabelle auf der "Einserseite" einer 1:n-Beziehung.)  
  
4.  Ziehen Sie Elemente aus der übergeordneten Tabelle der Beziehung aus angezeigt werden soll die **Datenquellen** auf das Formular.  
  
5.  Verknüpfte untergeordnete Tabellen werden als erweiterbare Knoten am unteren Ende der Spaltenliste einer übergeordneten Tabelle angezeigt. Ziehen Sie die anzuzeigenden Elemente aus einem solchen verknüpften Knoten auf das Formular.  
  
    > [!NOTE]
    >  Ziehen ein Element aus einem Knoten der obersten Ebene erstellt einen separaten unabhängig vom stagingstatus [BindingSource-Komponente](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) ist nicht erleichtert die verknüpften Datensätze zu navigieren. Um verknüpfte Daten zu binden, müssen Sie die Tabellen aus demselben hierarchischen Knoten auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Bearbeiten von typisierten "Datasets"](../data-tools/creating-and-editing-typed-datasets.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Vorgehensweise: Datennavigation mithilfe des BindingNavigator-Steuerelements in Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)