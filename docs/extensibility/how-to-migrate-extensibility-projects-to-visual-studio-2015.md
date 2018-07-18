---
title: 'Vorgehensweise: Migrieren von Erweiterungsprojekte für Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5adad311c1696d958902d9ad33ed1d1872606458
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127926"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Vorgehensweise: Migrieren von Erweiterungsprojekte für Visual Studio 2015
Hier wird erklärt, wie die Erweiterung zu aktualisieren.  
  
> [!IMPORTANT]
>  Wenn Sie eine Version für eine frühere Version von Visual Studio die Erweiterungsprojektmappe warten möchten, achten Sie darauf, dass eine Kopie zu erstellen, bevor Sie das Upgrade ausgeführt wird. Es möglicherweise schwierig, die aktualisierte Version den ursprünglichen Zustand zurück.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>So aktualisieren Sie eine Lösung für die Erweiterbarkeit  
  
1.  Mithilfe der Kopie möchten Sie aktualisieren, öffnen Sie es in der neuen Version. Sie werden informiert, dass das Upgrade nicht rückgängig gemacht werden.  
  
2.  Nach Abschluss des Upgrades ändern Sie den Pfad des externen Programms auf die neue Version von devenv.exe ein. Mit der rechten Maustaste in des Projektknoten der **Projektmappen-Explorer**, wählen Sie dann **Eigenschaften**. In der **Debuggen** Registerkarte, finden Sie im Textfeld durch **externes Programm starten** , und ändern Sie den Pfad der devenv.exe in Visual Studio 2015-Pfads, der etwa wie folgt aussehen sollte:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.14.0.dll. (Mit der rechten Maustaste in des Projektknoten der **Projektmappen-Explorer** und wählen Sie dann **hinzufügen / Reference**. Wählen Sie die **Erweiterungen** Registerkarte, und überprüfen Sie dann **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Erstellen Sie die Projektmappe. Die erstellten Dateien werden bereitgestellt:  
  
     **%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< author Name\>\\< Projektname\>\\< Projektversion\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Um ein Erweiterungsprojekt auf Verweisassemblys NuGet-VS-SDK zu aktualisieren  
  
1.  Bestimmen Sie die Verweisassemblys für VS-SDK muss das Projekt.  In **Projektmappen-Explorer**, erweitern Sie das Projekt **Verweise** Knoten, und überprüfen Sie die Liste der Projektverweise.  VS-SDK verweisen auf Assemblys haben das Präfix **Microsoft.VisualStudio** im Namen (z. B.: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Entfernen Sie die Verweisassemblys VS-SDK aus dem Projekt, indem Sie sie auswählen, mit der rechten Maustaste und **entfernen**.  
  
3.  Fügen Sie die NuGet-Versionen von VS-SDK-Verweisassemblys hinzu.  In der die **Projektmappen-Explorer Verweise** geöffneten Knoten die **NuGet-Pakete verwalten...**  Dialogfeld.  Wenn Sie weitere Informationen zu diesem Dialogfeld erfahren möchten, finden Sie unter [Paket-Manager-UI](/NuGet/Tools/Package-Manager-UI). Die Verweisassemblys VS-SDK sind auf veröffentlichte [nuget.org](http://www.nuget.org) von [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Mit **nuget.org** als Ihre **Paketquelle**, suchen Sie nach den Namen des NuGet-Paket die entspricht der gewünschten Verweisassembly (z. B.: Microsoft.VisualStudio.Shell.14.0) und installieren Sie es in Ihrer Projekt.  NuGet kann mehrere Verweisassemblys hinzufügen, um die ursprüngliche Assembly Abhängigkeiten zu erfüllen.  
  
     Falls gewünscht, können Sie die VS-SDK-Verweisassemblys auf einmal hinzufügen, indem Sie das VS-SDK installieren [Meta-Paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Sie können auch auf die Verwendung der NuGet-Version von VS-SDK-Buildtools wechseln. Dieses NuGet-Paket ist [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) und einmal hinzugefügt, um das Projekt wird die erforderlichen Tools und Zieldateien können Sie das Erweiterungsprojekt auf einem Computer ohne installierte VS-SDK zu erstellen.  
  
> [!NOTE]
>  Es ist nicht erforderlich, dass Sie der vorhandenen Erweiterbarkeit-Projekte zur Verwendung von NuGet-Verweisassemblys und Tools aktualisieren.  Sie können weiterhin erstellen mithilfe von Verweisassemblys und Tools, die mit dem VS-SDK installiert.