---
title: "Vorgehensweise: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe | Microsoft Docs"
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d7b8c8c9ca6dd964a58aa65b901d9219732179f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Gewusst wie: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe
  Sie können Konfigurationsdateien verwenden, zum Konfigurieren von Einstellungen, die spezifisch für Office-Projektmappen sind. Sie können die Einstellungen wie z. B. assemblybindungsrichtlinien, Remotingobjekte Debug und Trace-Einstellungen angeben.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Hinzufügen eine Konfigurationsdatei zu Office-Projekt  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  In der **Kategorien** Bereich, klicken Sie auf **allgemeine**.  
  
3.  In der **Vorlagen** klicken Sie im Bereich **Anwendungskonfigurationsdatei**.  
  
4.  In der **Namen** geben den gleichen Namen wie die Assembly mit der Erweiterung .config. Beispielsweise würde eine Konfigurationsdatei für eine Excel-Projekt-Assembly aufgerufen ExcelWorkbook1.dll ExcelWorkbook1.dll.config heißen.  
  
5.  Klicken Sie auf **Hinzufügen**.  
  
6.  Erstellen der Konfigurationsdatei entsprechend der Anwendung Konfigurationsdateischema an. Weitere Informationen finden Sie unter [Konfigurationsdateischema für .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Es sind keine besonderen Überlegungen für die Verwendung von Konfigurationsdateien mit Office-Projekten.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurationsdateischema für .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  