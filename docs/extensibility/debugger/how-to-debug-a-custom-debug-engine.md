---
title: 'Gewusst wie: Debuggen von benutzerdefinierten Debugmodul | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95a2db2bc5e8990f536abc851941c337a1dee277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Gewusst wie: Debuggen einer benutzerdefinierten Debugmodul
Ein Projekttyp startet die Debugging-Modul (DE) aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Methode. Dies bedeutet, dass die DE, unter der Kontrolle der Instanz von gestartet wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Steuern des Projekttyps. Allerdings diese Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE kann nicht gedebuggt werden. Im folgenden sind die Schritte, die Ihre benutzerdefinierte DE Debuggen können.  
  
> [!NOTE]
>  : In der Prozedur "Debuggen eines benutzerdefinierten Debuggen Datenbankmodul" müssen Sie warten, für das DE starten, bevor Sie anfügen können. Wenn Sie ein Meldungsfeld am Anfang der de, die angezeigt wird platzieren, wenn DE gestartet wird, können Sie zu diesem Zeitpunkt und deaktivieren Sie dann im Meldungsfeld, um den Vorgang fortzusetzen. Auf diese Weise können abfangen, alle Ereignisse für Deutschland.  
  
> [!WARNING]
>  Benötigen Sie, ob Sie Remotedebuggen installiert werden, bevor Sie die folgenden Verfahren ausführen können. Finden Sie unter [Remotedebuggen](../../debugger/remote-debugging.md) Details.  
  
### <a name="debugging-a-custom-debug-engine"></a>Debuggen einen benutzerdefinierten Debugmodul  
  
1.  Starten Sie den Remotedebugmonitor msvsmon.exe an.  
  
2.  Aus der **Tools** in msvsmon.exe, wählen Sie im Menü **Optionen** So öffnen die **Optionen** (Dialogfeld).  
  
3.  Wählen Sie die Option "keine Authentifizierung", und klicken Sie auf **OK**.  
  
4.  Starten einer Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und öffnen Sie das benutzerdefinierte DE-Projekt.  
  
5.  Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und Öffnen von Ihrem benutzerdefinierten Projekt, das die DE gestartet wird (für die Entwicklung, dies ist in der Regel in der experimentellen Registrierungsstruktur, die bei der Installation von VSIP eingerichtet ist).  
  
6.  In diesem zweiten Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], laden Sie eine Quelldatei aus Ihrem benutzerdefinierten Projekt, und starten Sie das Programm, das gedebuggt werden. Warten Sie einige Minuten, ermöglichen die DE zu laden, oder warten Sie, bis ein Haltepunkt erreicht wird.  
  
7.  In der ersten Instanz des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (mit dem DE-Projekt), wählen Sie **an den Prozess anhängen** aus der **Debuggen** Menü.  
  
8.  In der **an den Prozess anhängen** ändern Sie im Dialogfeld die **Transport** auf **Remote (systemeigen ohne Authentifizierung)**.  
  
9. Ändern der **Qualifizierer** auf den Namen des Computers (Hinweis: ist ein Verlauf von Einträgen, daher Sie diesen Namen nur einmal einzugeben müssen).  
  
10. In der **verfügbare Prozesse** Liste, wählen Sie die Instanz Ihrer de, die ausgeführt wird, und klicken Sie auf die **Anfügen** Schaltfläche.  
  
11. Nachdem die Symbole in Ihre DE geladen haben, platzieren Sie Haltepunkte im Code DE.  
  
12. Jedes Mal, wenn Sie beenden und anschließenden Neustarten des Debugprozesses, wiederholen Sie die Schritte 6 bis 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debuggen eines benutzerdefinierten Projekttyps  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Geben Sie im normalen Registrierungsstruktur und laden das Projekt Projekt (Dies ist, die Quelle der Projekttyp keine Instanziierung des Project-Typs).  
  
2.  Öffnen Sie die Projekteigenschaften, und wechseln Sie zu der **Debuggen** Seite. Für die **Befehl**, geben Sie den Pfad zu der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (Standardmäßig ist dies *[Laufwerk]*\Programme\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Für die **Befehlsargumente**, Typ `/rootsuffix exp` für die experimentelle Registrierungsstruktur (erstellt als VSIP installiert wurde).  
  
4.  Klicken Sie auf **OK** um die Änderungen zu übernehmen.  
  
5.  Starten Sie den Projekttyp, durch Drücken von F5. Hierdurch wird eine zweite Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  An diesem Punkt können Sie Haltepunkte in Ihrem Projekt Typ Quellcode platzieren.  
  
7.  In der zweiten Instanz des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], laden oder erstellen Sie eine neue Instanz des Project-Typs. Beim Laden oder erstellen können die festgelegten Haltepunkte anzusteuern sein.  
  
8.  Debuggen Sie den Projekttyp.  
  
9. Falls gewünscht, um den Prozess beim Starten einer bereitgestellten Kompatibilitätsrichtlinie zu debuggen, können Sie die Schritte ausführen, in der Prozedur "Debuggen eines benutzerdefinierten Debuggen Datenbankmodul" an Ihre DE angefügt werden soll, nachdem es gestartet wird. Dadurch haben Sie drei Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ausgeführt: eine für die Quelle des Projekts-Typ, einen zweiten für Ihre instanziierte Projekttyp und das dritte an Ihre DE angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)