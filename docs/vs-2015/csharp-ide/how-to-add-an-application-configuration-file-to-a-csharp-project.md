---
title: 'Vorgehensweise: Hinzufügen eine Anwendungskonfigurationsdatei zu einem C# Projekt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 481c1a66f3e025d3a29b2d5a1e39cd29bbb22490
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958151"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Vorgehensweise: Hinzufügen eine Anwendungskonfigurationsdatei zu einem C# Projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch Hinzufügen einer Anwendungskonfigurationsdatei (Datei „app.config“) zu einem C#-Projekt können Sie anpassen, wie die Common Language Runtime Assemblydateien sucht und lädt. Weitere Informationen zu Anwendungskonfigurationsdateien finden Sie unter [How the Runtime Locates Assemblies](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  Die Windows Store unterstützt keine <xref:System.Configuration>. Store-apps enthalten daher keine "App.config"-Vorlage.  
  
 Wenn Sie Ihr Projekt erstellen, die Entwicklungsumgebung kopiert automatisch Ihre Datei "App.config" ändert den Dateinamen der Kopie entsprechend Ihrer ausführbaren Datei und verschiebt die Kopie dann in das Verzeichnis "bin".  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>C#-Projekt eine Anwendungskonfigurationsdatei hinzu  
  
1.  Wählen Sie auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Erweitern Sie **installiert**, erweitern Sie **Visual C#-Elemente**, und wählen Sie dann die **Anwendungskonfigurationsdatei** Vorlage.  
  
3.  Geben Sie im Textfeld **Name** einen Namen ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.  
  
     Das Projekt wird eine Datei mit dem Namen "App.config" hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Anwendungseinstellungen (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Konfigurationsdateischema](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Konfigurieren von Apps](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Vorgehensweise: Konfigurieren einer App für eine .NET Framework-Version als Ziel](http://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Verwenden der Visual Studio-Entwicklungsumgebung für C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)