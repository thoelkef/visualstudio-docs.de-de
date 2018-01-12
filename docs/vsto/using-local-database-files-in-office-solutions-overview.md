---
title: "Verwendung lokaler Datenbankdateien in Office-Projektmappen (Übersicht) | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Übersicht über die Verwendung lokaler Datenbankdateien in Office-Lösungen
  Sie können eine Datenbankdatei, z. B. einer SQL Server Express (MDF) oder einer Microsoft Office Access (MDB)-Datei, in der Office-Projektmappe einschließen. Dies ermöglicht es den Benutzern zu eine lokale Datenbank in Situationen zu verwalten, in denen Verwendung einer zentralen Datenbank nicht erforderlich ist, z. B. in einer lokalen Inventory-Lösung ist, die auf nur einem einzelnen Computer verwendet wird.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>Importieren die Datenbankdatei in einem Projekt  
 Verwenden, um die Datenbankdatei in Ihr Projekt zu importieren, die **Data Source Configuration Wizard** So erstellen eine Datenquelle basierend auf die Datenbankdatei. Der Assistent fügt die Datenbankdatei und ein typisiertes Dataset zu Ihrem Projekt hinzu.  
  
## <a name="deploying-the-database-file"></a>Bereitstellen der Datenbankdatei  
 Die **Data Source Configuration Wizard** einen relativen Pfad verwendet, um Verbindungen mit der lokalen Datenbankdatei zu erstellen. Dadurch können Sie die Lösung von einem Computer in eine andere kopieren, wenn Sie die relativen Positionen der Dateien beibehalten.  
  
 Wenn Sie die Projektmappe auf einem Server bereitstellen und anschließend das Dokument an alle Endbenutzer verteilen, müssen Sie auch manuell verteilen die Datenbankdatei und installieren Sie es in der gleichen Position relativ zum Dokument. Dies bedeutet, dass der Endbenutzer das Dokument an einen neuen Speicherort auf dem Computer verschoben werden kann, es sei denn, er auch die Datenbankdatei verschiebt.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Lokale Datenbankdateien und das Dataset zwischenspeichern  
 In Projektmappen auf Dokumentebene für Microsoft Office Excel und Microsoft Office Word können Sie Datasets im Dokument zwischenspeichern, durch die Markierung der Dataset-Instanz mit dem Attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Wenn Sie die Datenbankdatei zum Projekt mit Hinzufügen der **Data Source Configuration Wizard**, ein typisiertes Dataset wird Ihrem Projekt automatisch hinzugefügt. Es ist nur selten notwendig, gelten <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> mit diesem Dataset, da die Daten bereits lokal auf dem Computer des Benutzers vorhanden ist. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)  
  
  