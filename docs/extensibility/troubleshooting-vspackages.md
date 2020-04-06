---
title: Fehlerbehebung bei VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698916"
---
# <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages
Im Folgenden finden Sie häufige Probleme, die Sie möglicherweise mit Ihrem VSPackage haben, und Tipps, um die Probleme zu beheben.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>So beheben Sie ein VSPackage, das Visual Studio vom Start

- Starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie im abgesicherten Modus.

   Um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus zu starten, geben Sie an einer Eingabeaufforderung **devenv.exe /safemode**ein.

   Während dieses Vorgangs werden keine VSPackages geladen, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]außer den VSPackages, die in enthalten sind.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>So beheben Sie ein VSPackage, das nicht geladen wird

1. Stellen Sie sicher, dass Sie den Registrierungsstamm verwenden, in dem das VSPackage registriert ist, um ausgeführt zu werden, in der Regel den experimentellen Registrierungsstamm.

    Weitere Informationen finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).

2. Wenn das VSPackage für die Ausführung im experimentellen Registrierungsstamm vorgesehen ist, stellen Sie sicher, dass Sie die experimentelle Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ausführen.

    Um die experimentelle Version auszuführen, geben Sie Folgendes in ein Befehlsfenster ein: **devenv /rootsuffix exp**.

3. Überprüfen Sie Ihre VSPackage-Registrierungseinträge.

    Weitere Informationen finden Sie unter [Registrieren von VSPackages](registering-and-unregistering-vspackages.md) und [Verwalten von VSPackages](../extensibility/managing-vspackages.md).

4. Öffnen Sie das **Ausgabefenster** der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Instanz, die das VSPackage nicht lädt. In diesem Fenster werden möglicherweise Informationen darüber angezeigt, warum das VSPackage nicht geladen werden kann.

   > [!NOTE]
   > Wenn Sie die experimentelle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] von aus der integrierten Entwicklungsumgebung (IDE) starten, überprüfen Sie das **Ausgabefenster** beider Versionen.

5. Überprüfen Sie das Aktivitätsprotokoll.

    Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).

6. Weitere Informationen zu Ausnahmen, die von der IDE ausgelöst werden, erhalten Sie, um die Ausnahmen zu aktivieren, auf **Ausnahmen** im **Menü Debuggen.** Wählen Sie im Dialogfeld **Ausnahmen** die Arten von Ausnahmen aus, zu denen Sie weitere Informationen erhalten möchten.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>So beheben Sie ein VSPackage, das sich nicht registriert

1. Stellen Sie sicher, dass sich die VSPackage-Assembly an einem vertrauenswürdigen Speicherort befindet. RegPkg kann Assemblys nicht an einem nicht vertrauenswürdigen oder teilweise vertrauenswürdigen Speicherort registrieren, z. B. einer Netzwerkfreigabe in der standardmäßigen .net-Sicherheitskonfiguration. Obwohl eine Warnung angezeigt wird, wenn ein Benutzer ein Projekt an einem nicht vertrauenswürdigen Speicherort erstellt, kann das Kontrollkästchen "Diese Meldung nicht erneut anzeigen" verhindern, dass diese Warnung erneut auftritt.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>So beheben Sie einen Befehl, der nicht sichtbar ist oder beim Klicken auf einen Befehl einen Fehler generiert

1. Führen Sie die neuen oder geänderten Menübefehle und die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bereits in der IDE bereits enthaltenen Befehle zusammen, indem Sie Folgendes an der Eingabeaufforderung eingeben: **devenv /rootsuffix Exp /setup**.

2. Stellen Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sicher, dass UI.dll für Ihr VSPackage gefunden werden kann.

   1. Suchen Sie die CLSID des VSPackage im Abschnitt Pakete der Registrierung:

        HKLM-Software-Microsoft-Visual\\*\<Studio-Version>*

   2. Stellen Sie sicher, dass der vom SatelliteDll-Unterschlüssel angegebene Pfad korrekt ist.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>So beheben Sie ein VSPackage, das sich unerwartet verhält

1. Legen Sie im Code Haltepunkte fest.

     Gute Ausgangspunkte für das Debuggen sind der Konstruktor und die Initialisierungsmethode. Sie können auch Haltepunkte in dem Bereich festlegen, den Sie auswerten möchten, z. B. einen Menübefehl. Um Haltepunkte zu aktivieren, müssen Sie unter dem Debugger ausgeführt werden.

    1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

    2. Aktivieren Sie im Dialogfeld **Eigenschaftenseiten** die Registerkarte **Debuggen.**

    3. Geben Sie im Feld **Befehlszeilenargumente** das Stammsuffix der Entwicklungsumgebung ein, auf das Ihr VSPackage abzielt. Um z. B. den experimentellen Build auszuwählen, geben Sie ein: **/RootSuffix Exp**.

    4. Klicken Sie im **Menü Debuggen** auf **Debuggen starten** oder drücken Sie F5.

        > [!NOTE]
        > Wenn Sie ein Projekt debuggen, erstellen oder laden Sie jetzt eine vorhandene Instanz Ihres Projekts.

2. Verwenden Sie das Aktivitätsprotokoll.

     Verfolgen Sie das VSPackage-Verhalten, indem Sie Informationen an wichtigen Punkten in das Aktivitätsprotokoll schreiben. Diese Technik ist besonders nützlich, wenn Sie ein VSPackage in einer Einzelhandelsumgebung ausführen. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).

3. Verwenden Sie öffentliche Symbole.

     Um die Lesbarkeit beim Debuggen zu verbessern, können Sie dem Debugger Symbole anfügen.

    1. Navigieren Sie im Menü **Extras/Optionen** zum Dialogfeld **Debugging/Symbols.**

    2. Fügen Sie diesen **Symboldateispeicherort (.pdb) hinzu:**

         `https://msdl.microsoft.com/download/symbols`

    3. Um die Leistung zu verbessern, geben Sie einen Symbolcacheordner an, z. B.:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>So beheben Sie ein fehlendes VSPackage oder eine seiner Abhängigkeiten

1. Stellen Sie bei verwaltetem Code sicher, dass die Referenzpfade korrekt sind.

   1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

   2. Wählen Sie die Registerkarte **Referenzen** im Dialogfeld **Eigenschaftenseiten** aus, und stellen Sie sicher, dass alle Pfade korrekt sind. Alternativ können Sie den **Objektbrowser** verwenden, um nach den referenzierten Objekten zu suchen.

        Für verwalteten Code können Sie [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) verwenden, um die Details fehlgeschlagener Assemblylasten anzuzeigen.

2. Suchen Sie für nicht verwalteten Code die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID des VSPackage im CLSID-Registrierungsknoten:

    HKLM-Software-Microsoft-Visual\\*\<Studio-Version>*

   Stellen Sie sicher, dass der InprocServer32-Eintrag den richtigen Pfad der VSPackage dll hat.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
