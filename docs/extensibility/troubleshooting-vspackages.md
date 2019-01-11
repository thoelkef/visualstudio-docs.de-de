---
title: Problembehandlung bei VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: 5ba413fa4b5a77c8c4f7fc9dfc9aa3c4ab87d31d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835970"
---
# <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages
Es folgen allgemeine Probleme, die Sie möglicherweise mit einem VSPackage und Tipps zum Beheben der Probleme.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Um ein VSPackage zu beheben, mit dem Visual Studio aus starten  
  
- Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus.  
  
   Zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Geben Sie im abgesicherten Modus an einer Eingabeaufforderung **devenv.exe SafeMode**.  
  
   Während dieses Vorgangs werden keine VSPackages geladen, mit Ausnahme der VSPackages, die in enthaltenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Um ein VSPackage zu beheben, die nicht geladen werden kann  
  
1. Stellen Sie sicher, dass Sie in der das VSPackage registriert ist, ausgeführt wird, in der Regel den experimentellen Registrierungsstamm Registrierungsstamm verwenden.  
  
    Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
2. Wenn das VSPackage gerichtet ist, führen Sie in der experimentellen Registrierungsstamm, stellen Sie sicher, dass Sie die experimentelle Version von ausgeführt werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    Um die experimentelle Version ausführen, geben Sie Folgendes in einem Befehlsfenster: **Devenv/rootsuffix exp**.  
  
3. Überprüfen Sie Ihre VSPackage-Registrierungseinträge.  
  
    Weitere Informationen finden Sie unter [Registrieren von VSPackages](registering-and-unregistering-vspackages.md) und [Verwalten von VSPackages](../extensibility/managing-vspackages.md).  
  
4. Öffnen der **Ausgabe** Fenster der Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tritt ein Fehler, die auf das VSPackage lädt. Informationen, warum das VSPackage nicht laden kann in diesem Fenster angezeigt werden.  
  
   > [!NOTE]
   >  Wenn Sie die experimentelle Version von starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE), überprüfen Sie die **Ausgabe** Fenster beider Versionen.  
  
5. Überprüfen Sie das Aktivitätsprotokoll.  
  
    Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).  
  
6. Weitere Informationen zu Ausnahmen, die von der IDE, klicken Sie auf **Ausnahmen** auf die **Debuggen** Menü, um die Ausnahmen zu aktivieren. In der **Ausnahmen** wählen Sie im Dialogfeld die Arten von Ausnahmen, die über die Sie benötigen Sie weitere Informationen.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Um ein VSPackage zu beheben, die nicht registriert ist  
  
1.  Stellen Sie sicher, dass die VSPackage-Assembly an einem vertrauenswürdigen Standort befindet. RegPkg kann nicht in eine nicht vertrauenswürdige oder teilweise vertrauenswürdige Speicherort, z. B. einer Netzwerkfreigabe, in der standardmäßigen Sicherheitskonfiguration für .net Assemblys zu registrieren. Obwohl eine Warnung angezeigt wird, wenn ein Benutzer ein Projekt in einem nicht vertrauenswürdigen Speicherort erstellt, kann das Kontrollkästchen "nicht diese Meldung erneut anzeigen" zu verhindern, dass diese Warnung erneut auftritt.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Um einen Befehl zu beheben, die nicht sichtbar ist, oder, einen Fehler generiert, wenn Sie einen Befehl klicken  
  
1. Die neue oder geänderte Menübefehle und die bereits in der IDE zusammenführen, geben Sie Folgendes an der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung: **Devenv/rootsuffix Exp/Setup**.  
  
2. Stellen Sie sicher, dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] UI.dll für Ihr VSPackage finden.  
  
   1.  Suchen Sie die CLSID des VSPackage, in der Pakete-Abschnitt der Registrierung:  
  
        HKLM\Software\Microsoft\Visual Studio\\*\<Version >* \Packages  
  
   2.  Stellen Sie sicher, dass der richtige Pfad durch den Unterschlüssel SatelliteDll angegeben wurde.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Eine VSPackage zu behandeln, die unerwartet verhält.  
  
1.  Legen Sie im Code Haltepunkte fest.  
  
     Gute Ausgangspunkte für das Debuggen sind der Konstruktor und die Initialisierungsmethode. Sie können auch Haltepunkte festlegen, die in den Bereich, z. B. einen Menübefehl auswerten möchten. Um Haltepunkte zu aktivieren, müssen Sie sich unter dem Debugger ausführen.  
  
    1.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
    2.  Auf der **Eigenschaftenseiten** wählen Sie im Dialogfeld die **Debuggen** Registerkarte.  
  
    3.  In der **Befehlszeilenargumente** geben die Stamm-Suffix der Entwicklungsumgebung, die das VSPackage abzielt. Um das experimentelle Build auswählen, geben Sie z. B.: **RootSuffix Exp**.  
  
    4.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen starten** oder drücken Sie F5.  
  
        > [!NOTE]
        >  Wenn Sie ein Projekt debuggen, erstellen Sie oder Laden Sie jetzt eine vorhandene Instanz des Projekts.  
  
2.  Verwenden des Aktivitätsprotokolls an.  
  
     Verfolgen Sie VSPackage-Verhalten, indem Sie das Schreiben von Informationen zum Aktivitätsprotokoll an wichtigen Punkten. Diese Technik ist besonders nützlich, wenn Sie eine VSPackage im einzelhandelsumfeld ausführen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Verwenden Sie die öffentlichen Symbole.  
  
     Zur Verbesserung der Lesbarkeit während des Debuggens können Sie Symbole an den Debugger anfügen.  
  
    1.  Aus der **Extras/Optionen** Menü navigieren Sie zu der **Debuggen/Symbolen** Dialogfeld.  
  
    2.  Fügen Sie Folgendes **für Symboldateien (.pdb) Speicherort**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Geben Sie einen Symbol-Cache-Ordner, z. B. zur Verbesserung der Leistung:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Um ein VSPackage fehlt oder eine ihrer Abhängigkeiten zu beheben  
  
1. Für verwalteten Code sicher, dass die Verweispfade richtig sind.  
  
   1.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
   2.  Wählen Sie die **Verweise** Registerkarte die **Eigenschaftenseiten** im Dialogfeld, und stellen Sie sicher, dass für alle Pfade richtig sind. Alternativ können Sie die **Objektkatalog** um die referenzierten Objekte zu suchen.  
  
        Für verwalteten Code können Sie die [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) zum Anzeigen der Details der fehlgeschlagene Assembly lädt.  
  
2. Suchen Sie für nicht verwalteten Code, die CLSID des VSPackage in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Knoten der CLSID-Registrierung:  
  
    HKLM\Software\Microsoft\Visual Studio\\*\<Version >* \CLSID  
  
   Stellen Sie sicher, dass der Eintrag InprocServer32 den richtigen Pfad für die VSPackage-Dll verfügt.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)