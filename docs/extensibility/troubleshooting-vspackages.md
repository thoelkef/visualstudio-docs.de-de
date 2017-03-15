---
title: Problembehandlung bei VSPackages | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>Problembehandlung bei VSPackages
Folgendes sind die häufigsten Probleme, die Sie möglicherweise mit der VSPackage und Tipps zur Fehlerbehebung.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Um ein VSPackage behandeln, die Visual Studio gestartet wird  
  
-   Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus.  
  
     Starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Geben Sie im abgesicherten Modus befinden, in einer Befehlszeile **devenv.exe/SafeMode**.  
  
     Während dieses Vorgangs werden keine VSPackages geladen, mit Ausnahme der VSPackages, die in enthalten sind [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Um ein VSPackage behandeln, die nicht geladen werden kann  
  
1.  Stellen Sie sicher, dass Sie den Registrierungsstamm arbeiten in dem das VSPackage registriert ist, ausgeführt wird, in der Regel die experimentelle Registrierungsstamm.  
  
     Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
2.  Wenn VSPackage vorgesehen ist, wenn Sie in der experimentellen Registrierungsstamm ausführen, stellen Sie sicher, dass Sie die Testversion von ausgeführt werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Um die experimentelle Version ausführen, geben Sie Folgendes in einem Befehlsfenster: **Devenv/rootsuffix exp**.  
  
3.  Überprüfen Sie Ihre VSPackage-Registrierungseinträge.  
  
     Weitere Informationen finden Sie unter [registrieren VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) und [Verwalten von VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Öffnen Sie die **Ausgabe** Fenster der Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die zum Laden des VSPackages fehlschlägt. Informationen, warum das VSPackage fehlgeschlagen ist, laden kann in diesem Fenster angezeigt werden.  
  
    > [!NOTE]
    >  Wenn Sie die Testversion von starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE), überprüfen Sie die **Ausgabe** Fenster beider Versionen.  
  
5.  Überprüfen Sie das Aktivitätsprotokoll.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Weitere Informationen zu Ausnahmen, die von der IDE, klicken Sie auf **Ausnahmen** auf der **Debuggen** Menü, um Ausnahmen zu aktivieren. In der **Ausnahmen** wählen Sie im Dialogfeld die Arten von Ausnahmen, die zu dem Sie weitere Informationen möchten.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Um ein VSPackage behandeln, die nicht registriert  
  
1.  Stellen Sie sicher, dass die VSPackage-Assembly an einem vertrauenswürdigen Speicherort befindet. RegPkg kann nicht in einem nicht vertrauenswürdigen oder teilweise vertrauenswürdigen Speicherort, z. B. eine Netzwerkfreigabe, in der Standardkonfiguration für .net Security Assemblys zu registrieren. Obwohl eine Warnung angezeigt wird, wenn ein Benutzer ein Projekt in einem nicht vertrauenswürdigen Speicherort erstellt, kann das Kontrollkästchen "nicht diese Meldung erneut anzeigen" zu verhindern, dass diese Warnung nicht wieder auftritt.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Beheben Sie einen Befehl, der nicht sichtbar ist, oder, einen Fehler generiert, wenn Sie einen Befehl klicken  
  
1.  Die neue oder geänderte Menübefehle und den bereits in der IDE zusammenführen, geben Sie Folgendes an der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Command Prompt: **Devenv/rootsuffix Exp/Setup**.  
  
2.  Stellen Sie sicher, dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] UI.dll für Ihr VSPackage finden.  
  
    1.  Finden Sie die CLSID des VSPackage wird im Abschnitt "Pakete" der Registrierung:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<Version >*\Packages  
  
    2.  Stellen Sie sicher, dass der von den Unterschlüssel SatelliteDll angegebene Pfad richtig ist.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Ein VSPackage zu beheben, die sich unerwartet verhält.  
  
1.  Legen Sie im Code Haltepunkte fest.  
  
     Stellen einen guten Ausgangspunkt für das Debuggen werden der Konstruktor und die Initialisierungsmethode. Sie können auch Haltepunkte in den Bereich festlegen, z. B. einen Menübefehl ausgewertet werden soll. Um Haltepunkte zu aktivieren, müssen Sie den Debugger ausführen.  
  
    1.  Auf der **Projekt** Menü klicken Sie auf **Eigenschaften**.  
  
    2.  Auf der **Eigenschaftenseiten** wählen Sie im Dialogfeld die **Debuggen** Registerkarte.  
  
    3.  In der **Befehlszeilenargumente** geben die Stamm-Suffix der Entwicklungsumgebung, die das VSPackage abzielt. Geben Sie z. B. zum Auswählen der Projektfunktion: **RootSuffix Exp**.  
  
    4.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen** oder drücken Sie F5.  
  
        > [!NOTE]
        >  Wenn Sie ein Projekt debuggen, erstellen Sie oder Laden Sie jetzt eine vorhandene Instanz des Projekts.  
  
2.  Verwenden Sie das Aktivitätsprotokoll.  
  
     Schreiben von Informationen in das Aktivitätsprotokoll an wichtigen Punkten verfolgen Sie VSPackage-Verhalten. Diese Technik ist besonders nützlich, wenn Sie ein VSPackage in einer Umgebung ausführen. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Verwenden Sie Öffentliche Symbole.  
  
     Zur Verbesserung der Lesbarkeit während des Debuggens können Sie Symbole für den Debugger anfügen.  
  
    1.  Aus der **Extras/Optionen** Menü navigieren Sie zu der **Debuggen/Symbole** Dialogfeld.  
  
    2.  Fügen Sie diese **Symboldateien (.pdb) Speicherort**:  
  
         [http://msdl.Microsoft.com/Download/Symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Zur Verbesserung der Leistung Geben Sie beispielsweise einen Symbol-Cache-Ordner:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Behandlung von fehlenden VSPackages oder eine ihrer Abhängigkeiten  
  
1.  Stellen Sie für verwalteten Code sicher, dass die Verweispfade richtig sind.  
  
    1.  Auf der **Projekt** Menü klicken Sie auf **Eigenschaften**.  
  
    2.  Wählen Sie die **Verweise** Registerkarte der **Eigenschaftenseiten** (Dialogfeld), und stellen Sie sicher, dass alle Pfade richtig sind. Alternativ können Sie die **Objektkatalog** um die referenzierten Objekte zu suchen.  
  
         Bei verwaltetem Code können Sie die [Fuslogvw.exe (Assembly Binding Log Viewer)](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296) die Details der fehlgeschlagenen Assembly lädt angezeigt.  
  
2.  Suchen Sie für nicht verwalteten Code, die CLSID des VSPackage in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Knoten der CLSID-Registrierung:  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<Version >*\CLSID  
  
 Stellen Sie sicher, dass der Eintrag InprocServer32 den richtigen Pfad für die VSPackage-Dll verfügt.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)
