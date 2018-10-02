---
title: 'Vorgehensweise: Erstellen von Datentabellen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 596c2760e100bc45eefdde10743b3d9b45490b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521441"
---
# <a name="how-to-create-data-tables"></a>Gewusst wie: Erstellen von Datentabellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daten können in <xref:System.Data.DataTable>-Objekten im Arbeitsspeicher gespeichert werden. (Datasets bestehen aus <xref:System.Data.DataTable>-Objekten.) Erstellen Sie in der Regel neue Datentabellen mit TableAdapters der [TableAdapter-Konfigurations-Assistenten](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) oder ziehen Datenbankobjekte aus **Server-Explorer** auf die **Dataset-Designer** .  
  
 Datentabellen werden als Nebenprodukt beim Erstellen neuer TableAdapters im erstellt die [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) , aber sie können auch unabhängig voneinander erstellt werden. Erstellen Sie eine eigenständige Datentabelle durch Ziehen einer <xref:System.Data.DataTable> -Objekt aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.  
  
> [!NOTE]
>  Zum programmgesteuerten Erstellen von Datentabellen finden Sie unter [Erstellen einer "DataTable"](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Erstellen einer Datentabelle mit TableAdapter  
 Datentabellen mit TableAdapters enthalten Methoden, die die Tabelle mit Daten füllen und Änderungen in die zugrunde liegende Datenbank eintragen. Erstellen von TableAdapters mit dem **TableAdapter-Konfigurations-Assistenten** oder ziehen Datenbankobjekte aus **Server-Explorer** auf die **Dataset-Designer**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>So erstellen Sie eine neue Datentabelle mit TableAdapter  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Ziehen Sie eine **TableAdapter** aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.  
  
     Die **TableAdapter-Konfigurations-Assistenten** wird geöffnet.  
  
3.  Durchlaufen Sie den Assistenten. Weitere Informationen finden Sie unter [TableAdapter-Konfigurations-Assistenten](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>So erstellen Sie eine neue Datentabelle mit einem TableAdapter unter Verwendung des Server-Explorers  
  
1.  Öffnen Sie das Dataset in den **Datenquellen-Designer**.  
  
2.  Ziehen Sie ein Datenbankobjekt (z. B. eine Tabelle) aus **Server-Explorer** auf die **Dataset-Designer**.  
  
## <a name="creating-a-standalone-datatable"></a>Erstellen einer eigenständigen Datentabelle  
 Damit eigenständige Tabellen mit Daten gefüllt werden, muss eine `Fill`-Logik implementiert werden. Informationen zum Füllen eigenständiger Datentabellen mit Daten finden Sie unter [Auffüllen eines Datasets mit einen "DataAdapter"](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>So erstellen Sie eine neue eigenständige Datentabelle  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**.  
  
2.  Ziehen Sie eine <xref:System.Data.DataTable> aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.  
  
3.  Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Spalten zu einer "DataTable"](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Data.DataTable>   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Bearbeiten von typisierten "Datasets"](../data-tools/creating-and-editing-typed-datasets.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Datenquellenfenster](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)