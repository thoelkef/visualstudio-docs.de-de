---
title: Deinstallieren von Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b84cff997e24882903abae048dbdd5c3c16f7e17
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834828"
---
# <a name="uninstall-visual-studio"></a>Deinstallieren von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [deinstallieren Sie Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Diese Seite führt Sie durch die Deinstallation von Visual Studio 2015, eine frühere Version von unserer integrierten Suite von Produktivitätstools für Entwickler.

##  <a name="uninstalling"></a>
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>So deinstallieren Sie Visual Studio mit der Deinstallation von "standard"-Methode

1. Wählen Sie in der **Systemsteuerung** auf der Seite **Programme und Funktionen** die Produktversion aus, die Sie deinstallieren möchten, und wählen Sie anschließend **Ändern** aus.

2. Wählen Sie im Setup-Assistenten **Deinstallieren** aus, wählen Sie **Ja** aus, und befolgen Sie anschließend die übrigen Anweisungen des Assistenten.

   Dieser Standard oder Standardmethode hinterlässt einige Elemente, die Ihre ersten Installations von Visual Studio ursprünglich installiert hat (z. B. die Microsoft .NET Framework, Microsoft Visual C++ Redistributables, Microsoft SQL Server, usw.).   Wir lassen diese installiert, da viele andere Anwendungen, die von ihnen abhängig sind. Allerdings sollten Sie diese zu entfernen, wählen Sie ihren Eintrag im **Programme und Funktionen**, und entfernen Sie alle einzeln.

#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>So deinstallieren Sie Visual Studio und alle anderen zugehörigen Dateien (d. h. Deinstallieren fast aller Elemente)

1.  Suchen Sie die Visual Studio-.exe-Datei (z.B. "vs_enterprise.exe" Suchen).

    > [!NOTE]
    >  Die Datei sollte in einem Unterordner von "%ProgramData%\Package Cache", z. B. sein: C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe

2.  Führen Sie die .exe-Datei mit der / uninstall/force-Parameter in der Befehlszeile.

     Führen Sie z. B. ```vs_enterprise.exe /uninstall /force```, wird die Visual Studio und die meisten Kernkomponenten, die zurückgelassen werden bei einer standarddeinstallation entfernt. Allerdings werden nicht entfernt alle zusätzliche Inhalte, Visual Studio-Add-Ons und-Erweiterungen (z. B. Visual Studio-Updates, und andere optionalen Komponenten) installieren können.

    > [!TIP]
    > Alternativ können Sie die "**Total Uninstaller**" tool, um alles zu entfernen, die Visual Studio oder Updates für Visual Studio installiert haben. D.h., jede Version von Visual Studio 2013 oder höher. Wenn Sie mehr erfahren möchten, finden Sie unter den [Visual Studio-Deinstallationstool](https://github.com/Microsoft/VisualStudioUninstaller/releases) auf GitHub.

#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>So deinstallieren Sie Visual Studio im unbeaufsichtigten oder im passiven Modus (d. h. um die Deinstallation von der Quelle)

1.  Öffnen Sie die Windows-Eingabeaufforderung auf dem Computer, auf dem Visual Studio installiert ist.

2.  Geben Sie folgende Parameter ein:

     *DVDRoot* \\< Installationsdatei\> \</quiet&#124;/passive > [/ norestart] / uninstall

#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Rollback zu einer vorherigen Version oder die Version von Visual Studio

1. Deinstallieren von Visual Studio mithilfe der in diesem Thema aufgeführten Methoden.

   > [!WARNING]
   >  Deinstallieren eines aktuellen Release von Visual Studio (oder ein Visual Studio-Update) und dann Installieren einer früheren Version funktioniert möglicherweise nicht wie erwartet.
   >
   >  Das Ergebnis hängt von der die Version oder die Version von Visual Studio installiert ist, welche Versionen der Komponenten installiert sind, welche Produkte installiert sind, die Abhängigkeiten entweder über die Visual Studio-Version oder die zugehörigen Komponenten möglicherweise und schließlich auf Welche frühere Visual Studio-Version, die Sie installieren oder erneut installieren möchten.  Aufgrund all dieser Variablen wird bei eine standarddeinstallation häufig lassen Komponenten, die mit früheren Versionen von Visual Studio oder Versionen möglicherweise nicht funktioniert.
   >
   >  Für optimale Ergebnisse sollten daher mit der [Visual Studio-Deinstallationstool](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Installieren Sie, oder installieren Sie die frühere Version von Visual Studio, die Sie verwenden möchten.

   Auch wenn Sie eine frühere Version von Visual Studio installieren, das Setup-Programm weiterhin versucht möglicherweise eine neuere Version verwenden oder freigeben, wenn eine verfügbar ist. Weitere Informationen finden Sie unter den [Vorgehensweise: Installieren einer bestimmten Version von Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) Thema.

## <a name="see-also"></a>Siehe auch
 [Installieren von Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)