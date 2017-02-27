---
title: "Gewusst wie: Debuggen einer benutzerdefinierten Debugmodul | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Debuggen"
  - "Debuggen von benutzerdefinierten Debugmodule [Debugging-SDK]"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Gewusst wie: Debuggen einer benutzerdefinierten Debugmodul
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projekttyp startet das Debugmodul \(DE\) aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>\-Methode.  Dies bedeutet, dass unter DE Kontrolle der Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Projekttyp steuernd gestartet wird.  Allerdings kann diese Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE nicht möglich.  Was sind im Folgenden werden die Schritte, um es Ihnen zu ermöglichen, benutzerdefinierte DE zu debuggen.  
  
> [!NOTE]
>  :     Im „module“ Debuggen auf Debugging benutzerdefinierten Prozedur müssen Sie auf DE warten, bevor Sie beginnen daran anfügen können.  Wenn Sie am Anfang DEs eines Meldungsfelds, der angezeigt wird, wenn DE beginnt, können Sie an dieser Stelle und dann Anfügen an klar das Meldungsfeld, um fortfahren zu können.  Auf diese Weise können Sie alles DE events abfangen.  
  
> [!WARNING]
>  Sie müssen das Remotedebuggen installiert haben, bevor Sie die folgenden Schritte ausführen.  Ausführliche Informationen finden Sie unter [Remotedebugging](../../debugger/remote-debugging.md).  
  
### Debuggen eines benutzerdefinierten Moduls Debuggen  
  
1.  Starten Sie den Remotedebugmonitor \(msvsmon.exe.  
  
2.  Klicken Sie im Menü **Extras** , wählen Sie msvsmon.exe **Optionen** , um den **Optionen** Dialogfeld zu öffnen.  
  
3.  Wählen Sie die Option „Keine Authentifizierung“ aus, und klicken Sie auf **OK**.  
  
4.  Starten einer Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , und öffnen Sie benutzerdefinierte DE project.  
  
5.  Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , und öffnen Sie das Projekt der benutzerdefinierten DE gestartet wird \(für Entwicklungs\-, ist dies in der Regel in der experimentellen Registrierungshiven eingerichtet ist, die Partner, wenn installiert wird\).  
  
6.  In diesem zweiten Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], laden Sie eine Quelldatei des benutzerdefinierten Projekt\- und starten Sie das Programm gedebuggt werden soll.  Warten Sie einige DE Momente geladen oder Wartevorgang kann, bis ein Haltepunkt erreicht ist.  
  
7.  Im ersten Fall von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(project\) mit dem DE **An den Prozess anhängenDebuggen** , wählen Sie im Menü.  
  
8.  Ändern Sie im Dialogfeld **An den Prozess anhängenTransport** zu **Remote \(systemeigen ohne Authentifizierung\)**.  
  
9. Ändern Sie den Namen des Computers **Qualifizierer** \(Hinweis: Es gibt einen Verlauf von Einträgen. Daher müssen Sie diesen Namen nur einmal eingeben\).  
  
10. Wählen Sie in der Liste **Verfügbare Prozesse** die Instanz ausgeführt wird, die DEs aus, und klicken Sie auf die Schaltfläche **Anfügen** .  
  
11. Nachdem die Symbole in DE geladen haben, fügen Sie Haltepunkte in DE Code.  
  
12. Jedes Mal, wenn Sie den Debugprozess beendet und dann neu gestartet, wiederholen Sie die Schritte 6 bis 10.  
  
### Debuggen eines benutzerdefinierten Projekttyp  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in den normalen Registrierungshiven und laden Sie das Projekt Projekttyp \(dies ist die Quelle für den Projekttyp keine Instanziierung vom Projekttyp\).  
  
2.  Öffnen Sie die Projekteigenschaften und wechseln Sie zur **Debuggen** Seite.  Für **Befehl**geben Sie den Pfad zum [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ein \(standardmäßig ist dies *\[Laufwerk\]*\\ Programme \\ Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8 \\ Common7 \\ IDE \\ devenv.exe\).  
  
3.  Für **Befehlsargumente**Typ `/rootsuffix Ausdruck` der experimentellen Registrierungshive \(erstellt, als Partner installiert wurde\).  
  
4.  Klicken Sie auf **OK**, um die Änderungen zu übernehmen.  
  
5.  Starten Sie den Projekttyp, indem Sie F5 drücken.  Dies startet eine zweite Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  An diesem Punkt können Sie Haltepunkte im Quellcode Projekttyp einfügen.  
  
7.  In der zweiten Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]laden, oder erstellen Sie eine neue Instanz des Projekttyps.  Während der Ladevorgang bzw. seit der Erstellung können die Haltepunkte erreicht.  
  
8.  Debuggen Sie den Projekttyp.  
  
9. Wenn Sie das Debuggen starten den Prozess der DE, können Sie die Schritte im Gewohnheits\-Debugen Debuggen „module“ \- Prozedur ausführen, um DE anzufügen, nachdem es gestartet wurde.  Dadurch haben Sie drei Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ausführung: Quelle Projekttyp einen für die eine Sekunde, für den instanziierten Projekttyp und eine dritte angefügt. DE  
  
## Siehe auch  
 [Erstellen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/creating-a-custom-debug-engine.md)