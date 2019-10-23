---
title: Problembehandlung bei VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94cb575969f232c9b4d60e7ddc93f9f727132951
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718712"
---
# <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages
Im folgenden finden Sie häufige Probleme, die Sie möglicherweise mit Ihrem VSPackage und Tipps zum Beheben der Probleme haben.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>So beheben Sie Probleme mit einem VSPackage, das den Start von Visual Studio beibehält

- Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus.

   Wenn Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus starten möchten, geben Sie an einer Eingabeaufforderung **devenv. exe/safemode**ein.

   Während dieses Vorgangs werden keine VSPackages geladen, außer den VSPackages, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthalten sind.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>So beheben Sie Probleme mit einem VSPackage, das nicht geladen wird

1. Stellen Sie sicher, dass Sie den Registrierungs Stamm verwenden, in dem das VSPackage für die Durchführung registriert ist, in der Regel der experimentelle Registrierungs Stamm.

    Weitere Informationen finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).

2. Wenn das VSPackage für die Ausführung im experimentellen Registrierungs Stamm bestimmt ist, stellen Sie sicher, dass Sie die experimentelle Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen.

    Um die experimentelle Version auszuführen, geben Sie Folgendes in einem Befehlsfenster ein: **devenv/rootsuffix Exp**.

3. Überprüfen Sie die Registrierungseinträge für das VSPackage.

    Weitere Informationen finden Sie unter [Registrieren von VSPackages](registering-and-unregistering-vspackages.md) und [Verwalten von VSPackages](../extensibility/managing-vspackages.md).

4. Öffnen Sie das **Ausgabe** Fenster der Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], die das VSPackage nicht laden kann. Informationen dazu, warum das VSPackage nicht geladen werden kann, werden möglicherweise in diesem Fenster angezeigt.

   > [!NOTE]
   > Wenn Sie die experimentelle Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) starten, überprüfen Sie das **Ausgabe** Fenster beider Versionen.

5. Überprüfen Sie das Aktivitätsprotokoll.

    Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../extensibility/how-to-use-the-activity-log.md).

6. Weitere Informationen zu von der IDE ausgelösten Ausnahmen erhalten Sie, indem Sie im Menü **Debuggen** auf **Ausnahmen** klicken, um die Ausnahmen zu aktivieren. Wählen Sie im Dialogfeld **Ausnahmen** die Typen von Ausnahmen aus, zu denen Sie weitere Informationen wünschen.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>So beheben Sie Probleme mit einem VSPackage, das nicht registriert ist

1. Stellen Sie sicher, dass sich die VSPackage-Assembly an einem vertrauenswürdigen Speicherort befindet. Regpkg kann keine Assemblys an einem nicht vertrauenswürdigen oder teilweise vertrauenswürdigen Speicherort registrieren, z. b. eine Netzwerkfreigabe in der standardmäßigen .net-Sicherheitskonfiguration Obwohl eine Warnung angezeigt wird, wenn ein Benutzer ein Projekt an einem nicht vertrauenswürdigen Speicherort erstellt, kann das Kontrollkästchen "Diese Meldung nicht mehr anzeigen" verhindern, dass diese Warnung erneut auftritt.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>So beheben Sie einen Befehl, der nicht sichtbar ist oder einen Fehler generiert, wenn Sie auf einen Befehl klicken

1. Führen Sie die neuen oder geänderten Menübefehle und die bereits in der IDE vorhandenen Befehle aus, indem Sie an der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung Folgendes eingeben: **devenv/rootsuffix Exp/Setup**.

2. Stellen Sie sicher, dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "UI. dll" für das VSPackage finden kann.

   1. Suchen Sie im Abschnitt "Pakete" der Registrierung nach der CLSID des VSPackage:

        Hklm\software\microsoft\visual Studio \\ *\<version >* \packages

   2. Überprüfen Sie, ob der durch den Unterschlüssel satellitedll angegebene Pfad richtig ist.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>So beheben Sie Probleme bei einem VSPackage, das sich unerwartet verhält

1. Legen Sie im Code Haltepunkte fest.

     Gute Ausgangspunkte für das Debuggen sind der Konstruktor und die Initialisierungs Methode. Sie können auch Breakpoints in dem Bereich festlegen, den Sie auswerten möchten, z. b. einen Menübefehl. Um Breakpoints zu aktivieren, müssen Sie unter dem Debugger ausgeführt werden.

    1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

    2. Wählen Sie im Dialogfeld **Eigenschaften Seiten** die Registerkarte **Debuggen** aus.

    3. Geben Sie im Feld **Befehlszeilenargumente** das Stamm Suffix der Entwicklungsumgebung ein, die das VSPackage als Ziel hat. Geben Sie z. b. Folgendes ein, um den experimentellen Build auszuwählen: **/RootSuffix Exp**.

    4. Klicken Sie im Menü **Debuggen** auf **Debugging starten** , oder drücken Sie F5.

        > [!NOTE]
        > Wenn Sie ein Projekt Debuggen, erstellen oder laden Sie jetzt eine vorhandene Instanz des Projekts.

2. Verwenden Sie das Aktivitätsprotokoll.

     Verfolgen Sie das VSPackage-Verhalten durch das Schreiben von Informationen in das Aktivitätsprotokoll an wichtigen Punkten. Diese Technik ist besonders nützlich, wenn Sie ein VSPackage in einer Einzelhandelsumgebung ausführen. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../extensibility/how-to-use-the-activity-log.md).

3. Verwenden Sie öffentliche Symbole.

     Um die Lesbarkeit beim Debuggen zu verbessern, können Sie Symbole an den Debugger anfügen.

    1. Navigieren Sie im Menü Extras **/Optionen** zum Dialogfeld **Debuggen** > Symbole.

    2. Fügen Sie den **Speicherort der Symbol Datei (PDB-Datei)** hinzu:

         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)

    3. Geben Sie zum Verbessern der Leistung einen Symbol Cache Ordner an, z. b.:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>So beheben Sie ein fehlendes VSPackage oder eine seiner Abhängigkeiten

1. Stellen Sie bei verwaltetem Code sicher, dass die Verweis Pfade korrekt sind.

   1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

   2. Wählen Sie im Dialogfeld **Eigenschaften Seiten** die Registerkarte **Verweise** aus, und stellen Sie sicher, dass alle Pfade korrekt sind. Alternativ können Sie den **Objektkatalog** verwenden, um nach den referenzierten Objekten zu suchen.

        Bei verwaltetem Code können Sie die [Datei "Fuslogvw. exe" (Assemblybindungs-Protokoll Anzeige)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) verwenden, um die Details der fehlerhaften assemblyladungen anzuzeigen.

2. Für nicht verwalteten Code suchen Sie die CLSID des VSPackage im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID-Registrierungs Knoten:

    Hklm\software\microsoft\visual Studio \\ *\<version >* \CLSID

   Stellen Sie sicher, dass der InprocServer32-Eintrag über den richtigen Pfad der VSPackage-dll verfügt.

## <a name="see-also"></a>Siehe auch
- [VSPackages](../extensibility/internals/vspackages.md)