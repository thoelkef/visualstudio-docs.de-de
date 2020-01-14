---
title: 'Vorgehensweise: Migrieren von Erweiterungs Projekten zu Visual Studio 2015 | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2f4926a503304491164635b983353ba7f3bb0f6
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915980"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Vorgehensweise: Migrieren von Erweiterungs Projekten zu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

So aktualisieren Sie die Erweiterung.  
  
> [!IMPORTANT]
> Wenn Sie beabsichtigen, eine Version der Erweiterungs Lösung für eine frühere Version von Visual Studio beizubehalten, stellen Sie sicher, dass Sie eine Kopie erstellen, bevor Sie Sie aktualisieren. Es ist möglicherweise schwierig, die aktualisierte Version auf den vorherigen Zustand zurückzusetzen.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>So aktualisieren Sie eine Erweiterbarkeits Lösung  
  
1. Öffnen Sie die Kopie, die Sie aktualisieren möchten, in der neuen Version. Sie werden darüber informiert, dass das Upgrade nicht rückgängig gemacht werden kann.  
  
2. Nachdem das Upgrade abgeschlossen ist, ändern Sie den Pfad des externen Programms in die neue Version von "devenv. exe". Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie dann **Eigenschaften**aus. Suchen Sie auf der Registerkarte **Debuggen** nach dem Textfeld, indem Sie **externes Programm starten** , und ändern Sie den Pfad von "devenv. exe" in den Pfad von Visual Studio 2015, der in etwa wie folgt aussehen sollte:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14,0 \ Common7\IDE\devenv.exe**  
  
3. Fügen Sie einen Verweis auf Microsoft. VisualStudio. Shell. 14,0. dll hinzu. (Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie dann **Hinzufügen/Verweis**aus. Wählen Sie die Registerkarte **Erweiterungen** aus, und überprüfen Sie **Microsoft. VisualStudio. Shell. 14,0**.)  
  
4. Erstellen Sie die Projektmappe. Die erstellten Dateien werden für Folgendes bereitgestellt:  
  
     **%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< Autor Name\>\\< Projektname** \>\\< Projekt Version\>\\.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>So aktualisieren Sie ein Erweiterbarkeits Projekt auf nuget vs SDK-Verweisassemblys  
  
1. Ermitteln der vs SDK-Verweisassemblys, die Ihr Projekt benötigt  Erweitern Sie in **Projektmappen-Explorer**den Knoten **Verweise** des Projekts, und überprüfen Sie die Liste der Projekt Verweise.  VS SDK References-Assemblys haben das Präfix " **Microsoft. VisualStudio** " im Namen (z. b. Microsoft. VisualStudio. Shell. 14,0).  
  
2. Entfernen Sie die vs SDK-Verweisassemblys aus dem Projekt, indem Sie Sie **auswählen und mit**der rechten Maustaste klicken  
  
3. Fügen Sie die nuget-Versionen der vs SDK-Verweisassemblys hinzu.  Öffnen Sie im Knoten **Projektmappen-Explorer Verweise** die **Pakete nuget-Pakete verwalten...** hinzu.  Weitere Informationen zu diesem Dialogfeld finden Sie unter Verwalten von [nuget-Paketen mithilfe des Dialog](/nuget/consume-packages/install-use-packages-visual-studio)Felds. Die vs SDK-Verweisassemblys werden von [visualstudioextensibility](https://www.nuget.org/profiles/VisualStudioExtensibility)auf [nuget.org](https://www.nuget.org/) veröffentlicht.  
  
4. Wenn Sie **nuget.org** als **Paketquelle**verwenden, suchen Sie nach dem nuget-Paketnamen, der der gewünschten Verweisassembly (z. b. Microsoft. VisualStudio. Shell. 14,0) entspricht, und installieren Sie Sie in Ihrem Projekt.  Nuget kann mehrere Verweisassemblys hinzufügen, um die Abhängigkeiten der ersten Assembly zu erfüllen.  
  
     Wenn Sie möchten, können Sie alle vs SDK-Verweisassemblys gleichzeitig hinzufügen, indem Sie das vs SDK- [Meta-Paket](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)installieren.  
  
5. Sie können auch mit der nuget-Version der vs SDK-Buildtools wechseln. Dieses nuget-Paket ist " [Microsoft. VSSDK. Buildtools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) " und wird nach dem Hinzufügen zu Ihrem Projekt die erforderlichen Tools und Zieldateien enthalten, damit Sie das Erweiterbarkeits Projekt auf einem Computer erstellen können, auf dem das vs SDK nicht installiert ist.  
  
> [!NOTE]
> Es ist nicht erforderlich, dass Sie vorhandene Erweiterbarkeits Projekte aktualisieren, um nuget-Verweisassemblys und-Tools zu verwenden.  Sie können weiterhin mithilfe von Verweisassemblys und Tools erstellt werden, die mit dem vs SDK installiert werden.
