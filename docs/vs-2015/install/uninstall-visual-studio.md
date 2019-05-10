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
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546901"
---
# <a name="uninstall-visual-studio"></a>Deinstallieren von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [Deinstallieren von Visual Studio](/visualstudio/install/uninstall-visual-studio).

Diese Seite führt Sie durch die Deinstallation von Visual Studio 2015, einer früheren Version unserer integrierten Suite von Produktivitätstools für Entwickler.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Deinstallieren von Visual Studio mithilfe der „Standard“-Deinstallationsmethode

1. Wählen Sie in der **Systemsteuerung** auf der Seite **Programme und Funktionen** die Produktversion aus, die Sie deinstallieren möchten, und wählen Sie anschließend **Ändern** aus.

2. Wählen Sie im Setup-Assistenten **Deinstallieren** aus, wählen Sie **Ja** aus, und befolgen Sie anschließend die übrigen Anweisungen des Assistenten.

   Bei dieser Standardmethode bleiben einige Komponenten erhalten, die bei der ersten Installation von Visual Studio ursprünglich installiert wurden (z.B. Microsoft .NET Framework, Microsoft Visual C++ Redistributables, Microsoft SQL Server usw.).   Diese bleiben installiert, da viele andere Anwendungen davon abhängig sind. Wenn Sie diese Komponenten allerdings auch entfernen möchten, wählen Sie den entsprechenden Eintrag unter **Programme und Funktionen** aus, und entfernen Sie die Komponenten dann einzeln nacheinander.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Deinstallieren von Visual Studio und allen anderen zugehörigen Dateien (d.h. Deinstallieren von fast allem)

1. Suchen Sie nach der EXE-Datei für Visual Studio (z.B. nach „vs_enterprise.exe“).

    > [!NOTE]
    > Die Datei sollte sich in einem Unterordner von „%ProgramData%\Package Cache“ befinden, z.B. „C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe“.

2. Führen Sie die EXE-Datei mit den Befehlszeilenparametern „/uninstall /force“ aus.

     Führen Sie beispielsweise ```vs_enterprise.exe /uninstall /force``` aus. Dadurch werden Visual Studio und die meisten Kernkomponenten entfernt, die bei einer Standarddeinstallation verbleiben. Allerdings werden nicht alle zusätzlichen Inhalte entfernt, die von Visual Studio-Add-Ons und -Erweiterungen installiert werden können (z.B. Visual Studio-Updates und andere optionale Komponenten).

    > [!TIP]
    > Alternativ können Sie das Tool **Total Uninstaller** verwenden, um alles zu entfernen, was mit Visual Studio oder Updates für Visual Studio installiert wurde, d.h., jede Version von Visual Studio 2013 oder höher. Weitere Informationen finden Sie unter [Visual Studio-Deinstallationstool](https://github.com/Microsoft/VisualStudioUninstaller/releases) auf GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Deinstallieren von Visual Studio im unbeaufsichtigten oder passiven Modus (d.h. Deinstallieren von der Quelle)

1. Öffnen Sie die Windows-Eingabeaufforderung auf dem Computer, auf dem Visual Studio installiert ist.

2. Geben Sie folgende Parameter ein:

     *DVDRoot* \\<Installationsdatei\> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Rollback auf eine frühere Version oder ein früheres Release von Visual Studio

1. Deinstallieren Sie Visual Studio mithilfe einer der in diesem Thema aufgeführten Methoden.

   > [!WARNING]
   > Das Deinstallieren eines aktuellen Release von Visual Studio (oder eines Visual Studio-Updates) und das anschließende Installieren eines früheren Release funktioniert möglicherweise nicht wie erwartet.
   >
   > Das Ergebnis hängt davon ab, welche Version oder welches Release von Visual Studio installiert ist, welche Versionen der Komponenten installiert sind, welche Produkte installiert sind, die möglicherweise vom Visual Studio-Release oder seinen Komponenten abhängig sind, und welche frühere Visual Studio-Version Sie installieren oder erneut installieren möchten.  Aufgrund all dieser Variablen verbleiben bei einer Standarddeinstallation häufig Komponenten, die mit früheren Visual Studio-Versionen oder -Releases möglicherweise nicht funktionieren.
   >
   > Deshalb wird für optimale Ergebnisse die Verwendung des [Visual Studio-Deinstallationstools](https://github.com/Microsoft/VisualStudioUninstaller/releases) empfohlen.

2. Führen Sie die Installation oder Neuinstallation einer früheren Version von Visual Studio durch, die Sie verwenden möchten.

   Auch wenn Sie eine frühere Version von Visual Studio installieren, versucht das Setupprogramm möglicherweise, eine neuere Version oder ein neueres Release (sofern verfügbar) zu verwenden. Ausführlichere Informationen finden Sie unter dem Thema [Gewusst wie: Installieren eines bestimmten Releases von Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md).

## <a name="see-also"></a>Siehe auch

- [Installieren von Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)