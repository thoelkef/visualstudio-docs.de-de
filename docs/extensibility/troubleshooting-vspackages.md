---
title: Problembehandlung bei VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146195"
---
# <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages
Es folgen allgemeine Probleme, die Sie möglicherweise mit Ihrem VSPackage und Tipps zum Beheben der Probleme.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Um ein VSPackage zu beheben, die Visual Studio wird verhindert, dass ab  
  
-   Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus.  
  
     Ans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus befinden, an der Eingabeaufforderung, geben Sie **devenv.exe/SafeMode**.  
  
     Während dieses Vorgangs werden keine VSPackages geladen, mit Ausnahme der VSPackages, die in enthaltenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Eine VSPackage zu beheben, die nicht geladen werden kann  
  
1.  Stellen Sie sicher, dass Sie in der das VSPackage registriert ist, ausgeführt wird, in der Regel den experimentellen Registrierungsstamm den Registrierungsstamm verwenden.  
  
     Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
2.  Wenn das VSPackage gerichtet ist, wenn Sie in der experimentellen Registrierungsstamm ausführen, stellen Sie sicher, dass Sie die experimentelle Version von ausgeführt werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Um die experimentelle Version auszuführen, geben Sie Folgendes in einem Befehlsfenster: **Devenv /rootsuffix exp**.  
  
3.  Überprüfen Sie Ihre VSPackage-Registrierungseinträge.  
  
     Weitere Informationen finden Sie unter [registrieren VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) und [Verwalten von VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Öffnen der **Ausgabe** Fenster der Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die das VSPackage lädt fehlschlägt. Informationen, warum das VSPackage nicht laden kann in diesem Fenster angezeigt werden.  
  
    > [!NOTE]
    >  Wenn Sie die experimentelle Version von starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) verwenden, Überprüfen der **Ausgabe** Fenster beider Versionen.  
  
5.  Überprüfen Sie das Aktivitätsprotokoll.  
  
     Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Weitere Informationen zu Ausnahmen, die von der IDE, klicken Sie auf **Ausnahmen** auf die **Debuggen** Menü, um die Ausnahmen zu aktivieren. In der **Ausnahmen** wählen Sie im Dialogfeld die Arten von Ausnahmen, die über die wünschen Sie weitere Informationen.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Eine VSPackage zu beheben, die nicht registriert  
  
1.  Stellen Sie sicher, dass die VSPackage-Assembly in einem vertrauenswürdigen Speicherort befindet. RegPkg kann Assemblys in ein nicht vertrauenswürdigen oder teilweise vertrauenswürdigen Speicherort, z. B. eine Netzwerkfreigabe, in der standardmäßigen .net Sicherheitskonfiguration nicht registrieren. Obwohl eine Warnung angezeigt wird, wenn ein Benutzer ein Projekt in einem nicht vertrauenswürdigen Speicherort erstellt, kann das Kontrollkästchen "führen Sie diese Meldung nicht mehr anzeigen" zu verhindern, dass diese Warnung nicht wieder auftritt.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Behandeln ein Befehls bereit, nicht sichtbar ist, oder, einen Fehler generiert, wenn Sie einen Befehl klicken  
  
1.  Die neue oder geänderte Menübefehle und die bereits in der IDE zusammenführen, geben Sie Folgendes an der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung: **Devenv /rootsuffix Exp/Setup**.  
  
2.  Stellen Sie sicher, dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finde UI.dll für Ihr VSPackage.  
  
    1.  Suchen Sie im Abschnitt "Pakete" der Registrierung die CLSID des VSPackage:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<Version >* \Packages  
  
    2.  Stellen Sie sicher, dass der von dem Unterschlüssel SatelliteDll angegebene Pfad korrekt ist.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Eine VSPackage zu beheben, die auf unerwartete Weise verhält  
  
1.  Legen Sie im Code Haltepunkte fest.  
  
     Gute Ausgangspunkte für das Debuggen sind der Konstruktor und die Initialisierungsmethode. Sie können auch Haltepunkte in den Bereich festlegen, wie einen Menübefehl ausgewertet werden sollen. Um Breakpoints zu aktivieren, müssen Sie im Debugger ausführen.  
  
    1.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
    2.  Auf der **Eigenschaftenseiten** wählen Sie im Dialogfeld die **Debuggen** Registerkarte.  
  
    3.  In der **Befehlszeilenargumente** geben das stammsuffix von der Entwicklungsumgebung, die das VSPackage abzielt. Um das experimentelle Build auswählen, geben Sie z. B.: **RootSuffix Exp**.  
  
    4.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen** oder drücken Sie F5.  
  
        > [!NOTE]
        >  Wenn Sie ein Projekt debuggen, erstellen Sie oder Laden Sie eine vorhandene Instanz des Projekts jetzt.  
  
2.  Verwenden Sie das Aktivitätsprotokoll.  
  
     VSPackage-Verhalten durch Schreiben von Informationen in das Aktivitätsprotokoll zu wichtigen Zeitpunkten zu verfolgen. Diese Technik ist besonders nützlich, wenn Sie eine VSPackage in einer Verkaufsversion-Umgebung ausführen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Verwenden Sie die öffentlichen Symbole.  
  
     Zur Verbesserung der Lesbarkeit während des Debuggens können Sie die Symbole an den Debugger anfügen.  
  
    1.  Aus der **Extras/Optionen** Menü, navigieren Sie zu der **Debuggen/Symbole** (Dialogfeld).  
  
    2.  Fügen Sie der **Symboldateien (.pdb) Dateispeicherort**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Um die Leistung zu verbessern, geben Sie z. B. einen Symbol-Cache-Ordner:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Ein VSPackage fehlt oder eine ihrer Abhängigkeiten beheben  
  
1.  Für verwalteten Code sicher, dass die Verweispfade richtig sind.  
  
    1.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
    2.  Wählen Sie die **Verweise** Registerkarte der **Eigenschaftenseiten** (Dialogfeld), und stellen Sie sicher, dass alle Pfade richtig sind. Alternativ können Sie die **Objektkatalog** , nach der referenzierten Objekte zu suchen.  
  
         Für verwalteten Code können Sie die [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) um die Details der fehlgeschlagene Assembly lädt anzuzeigen.  
  
2.  Suchen Sie für nicht verwalteten Code die CLSID des VSPackage in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Knoten der CLSID-Registrierungsschlüssel:  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<Version >* \CLSID  
  
 Stellen Sie sicher, dass der Eintrag InprocServer32 den richtigen Pfad für die VSPackage-Dll verfügt.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)