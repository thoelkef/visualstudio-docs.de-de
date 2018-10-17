---
title: 'Vorgehensweise: Starten Sie den TableAdapter-Konfigurations-Assistenten | Microsoft-Dokumentation'
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
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7f603789014239762f564c3b2391b99865d8f620
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261890"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Gewusst wie: Starten des TableAdapter-Konfigurations-Assistenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **TableAdapter-Konfigurations-Assistenten** erstellt und bearbeitet TableAdapters in stark typisierten "Datasets". Der Assistent erstellt TableAdapters auf der Grundlage von dort eingegebenen SQL-Anweisungen oder gespeicherten Prozeduren in der Datenbank. Ausgehend von SQL-Anweisungen, die Sie im Assistenten eingeben, kann der Assistent auch neue gespeicherte Prozeduren in der Datenbank erstellen.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Den TableAdapter-Konfigurations-Assistent zum Erstellen eines neuen TableAdapters starten  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Wenn Sie nicht über ein Dataset in Ihrem Projekt verfügen, finden Sie unter [erstellen und Konfigurieren von Datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Wenn Sie einen neuen TableAdapter erstellen, ziehen Sie eine **TableAdapter** -Objekt aus der **DataSet** auf der Registerkarte die **Toolbox** auf die **Dataset-Designer**.  
  
3.  Auf der **wählen Sie Ihre Datenverbindung** Seite, wählen Sie eine Datenverbindung aus der Liste der aktuell verfügbaren Verbindungen oder select **neue Verbindung** um eine neue Verbindung zu erstellen.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>So starten Sie den TableAdapter-Konfigurations-Assistent zum Bearbeiten eines vorhandenen TableAdapters  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Mit der rechten Maustaste des TableAdapter im der **Dataset-Designer** , und wählen Sie **konfigurieren**. Der Assistent öffnet die **SQL-Anweisungen generieren** Seite oder die **Befehle an vorhandene gespeicherte Prozeduren binden** je nach, wie der TableAdapter ursprünglich konfiguriert wurde.  
  
3.  Durchlaufen Sie den Assistenten.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Erstellen und Bearbeiten von typisierten "Datasets"](../data-tools/creating-and-editing-typed-datasets.md)   
 [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Vorgehensweise: Sortieren und Filtern von ADO.NET-Daten mit der BindingSource-Komponente in Windows Forms](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Vorgehensweise: Erstellen einer Suchtabelle mit der BindingSource-Komponente in Windows Forms](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)