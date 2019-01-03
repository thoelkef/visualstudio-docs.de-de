---
title: 'Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2015 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 456661c06934063041f06c36c20eee72d52c5b4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915334"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2015
Hier ist die Erweiterung zu aktualisieren.  
  
> [!IMPORTANT]
>  Wenn Sie beabsichtigen, eine Version der Erweiterungsprojektmappe für eine frühere Version von Visual Studio verwalten, achten Sie darauf, dass Sie eine Kopie zu erstellen, bevor Sie ein Upgrade durchführen. Es kann schwierig sein, die aktualisierte Version den ursprünglichen Zustand zurückzukehren sein.  
  
### <a name="to-upgrade-an-extensibility-solution"></a>So aktualisieren eine Lösung für die Erweiterbarkeit  
  
1.  Mit der Kopie soll, aktualisieren, öffnen Sie ihn in der neuen Version. Sie werden aufgefordert, dass das Upgrade nicht rückgängig gemacht werden.  
  
2.  Nachdem das Upgrade abgeschlossen ist, ändern Sie den Pfad des externen Programms, auf die neue Version der *devenv.exe*. Mit der rechten Maustaste des Knotens "Projekt" in der **Projektmappen-Explorer**, wählen Sie dann **Eigenschaften**. In der **Debuggen** Registerkarte, finden Sie im Textfeld durch **externes Programm starten** , und ändern Sie den Pfad des *devenv.exe* auf den Pfad des Visual Studio 2015, sollte die etwa wie folgt aussehen:  
  
     *%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe*  
  
3.  Hinzufügen eines Verweises auf *Microsoft.VisualStudio.Shell.14.0.dll*. (Mit der rechten Maustaste des Knotens "Projekt" in der **Projektmappen-Explorer** und wählen Sie dann **hinzufügen** > **Verweis**. Wählen der **Erweiterungen** Registerkarte, und überprüfen Sie dann **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Erstellen Sie die Projektmappe. Die erstellten Dateien werden in bereitgestellt:  
  
     *%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< author Name\>\\< Projektname\>\\< Projektversion\>\\*.  
  
### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Aktualisieren Sie ein Erweiterungsprojekt zum Verweisen auf Assemblys von NuGet-VS-SDK  
  
1.  Bestimmen Sie die VS-SDK-Verweisassemblys, die das Projekt benötigt.  In **Projektmappen-Explorer**, erweitern Sie das Projekt des **Verweise** Knoten und überprüfen Sie die Projekt-verweisen.  VS-SDK verweisen auf Assemblys haben das Präfix **Microsoft.VisualStudio** im Namen (z. B.: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Entfernen Sie dazu mit der rechten Maustaste, und wählen sie die VS-SDK-Verweisassemblys aus dem Projekt **entfernen**.  
  
3.  Fügen Sie die NuGet-Versionen der VS-SDK-Referenz-Assemblys hinzu.  In der die **Projektmappen-Explorer Verweise** Knoten, die **NuGet-Pakete verwalten** Dialogfeld.  Wenn Sie weitere Informationen zu diesem Dialogfeld möchten, finden Sie unter [-Paket-Manager-UI](/NuGet/Tools/Package-Manager-UI). Die VS-SDK-Verweisassemblys werden veröffentlicht, auf [nuget.org](http://www.nuget.org) von [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Mithilfe von **nuget.org** als Ihre **Paketquelle**, suchen Sie nach dem NuGet-Paketnamen an die gewünschte verweist die Verweisassembly entspricht (z. B.: Microsoft.VisualStudio.Shell.14.0), und installieren Sie es in Ihrem Projekt.  NuGet kann mehrere Verweisassemblys hinzufügen, um die anfängliche Abhängigkeiten der Assembly zu erfüllen.  
  
     Falls gewünscht, können Sie die VS-SDK-Verweisassemblys auf einmal hinzufügen, indem Sie die Installation von Visual Studio SDK [metapaket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Sie können auch wechseln, die NuGet-Version von Visual Studio SDK-Buildtools zu verwenden. Dieses NuGet-Paket ist [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) und nach dem Hinzufügen zu Ihrem Projekt wird die erforderlichen Tools und Dateien mit der Sie Ihr Erweiterungsprojekt auf einem Computer ohne das VS-SDK installiert erstellen können.  
  
> [!NOTE]
>  Es ist nicht erforderlich, dass Sie der vorhandenen Erweiterbarkeit-Projekte zur Verwendung von NuGet-Referenz-Assemblys und Tools aktualisieren.  Sie können weiterhin zum Erstellen mithilfe von Verweisassemblys und Tools, die mit dem Visual Studio SDK installiert.