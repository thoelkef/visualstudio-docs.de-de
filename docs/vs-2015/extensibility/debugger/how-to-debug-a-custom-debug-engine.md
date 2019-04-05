---
title: 'Vorgehensweise: Debuggen eine benutzerdefinierten Debug-Engine | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5292d2cde8a75a239f7a905d8cf5d80b09a8f61e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946449"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Vorgehensweise: Debuggen einer benutzerdefinierten Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Projekt startet die Debug-Engine (DE) aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Methode. Dies bedeutet, dass die DE, unter der Kontrolle der Instanz von gestartet wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] steuern den Projekttyp. Aber diese Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kann nicht debuggen, die DE. Nachfolgend werden die Schritte aus, damit Sie Ihre benutzerdefinierten DE Debuggen können.  
  
> [!NOTE]
>  :     In der Prozedur "Debuggen einer benutzerdefinierten Debug-Engine" müssen Sie warten, für das DE zum Starten, bevor Sie sie anfügen können. Wenn Sie ein Meldungsfeld nahe am Anfang Ihrer DE, die beim Start der DE angezeigt wird platzieren, können zu diesem Zeitpunkt Anfügen und deaktivieren Sie dann im Meldungsfeld, um den Vorgang fortzusetzen. Auf diese Weise können abfangen, alle DE-Ereignisse.  
  
> [!WARNING]
>  Benötigen Sie, ob Sie Remotedebuggen installiert, bevor Sie, die folgenden Verfahren versuchen. Finden Sie unter [Remotedebuggen](../../debugger/remote-debugging.md) Details.  
  
### <a name="debugging-a-custom-debug-engine"></a>Debuggen einer benutzerdefinierten Debug-Engine  
  
1.  Starten Sie den Remotedebugmonitor msvsmon.exe an.  
  
2.  Aus der **Tools** msvsmon.exe, wählen im Menü **Optionen** zum Öffnen der **Optionen** Dialogfeld.  
  
3.  Wählen Sie die Option "keine Authentifizierung", und klicken Sie auf **OK**.  
  
4.  Starten einer Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und öffnen Sie das benutzerdefinierte DE-Projekt.  
  
5.  Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und öffnen Sie das benutzerdefinierte Projekt, das die DE startet (für die Entwicklung, dies ist in der Regel in der experimentellen Registrierungsstruktur, die bei der Installation von VSIP eingerichtet ist).  
  
6.  In diesem zweiten Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], laden Sie eine Quelldatei aus Ihrem benutzerdefinierten Projekt, und starten Sie das Programm debuggt werden. Warten Sie einige Minuten, bis Sie ermöglichen die DE zu laden, oder warten Sie, bis ein Haltepunkt erreicht wird.  
  
7.  In der ersten Instanz des [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (mit dem DE-Projekt), wählen Sie **an den Prozess anhängen** aus der **Debuggen** Menü.  
  
8.  In der **an den Prozess anhängen** im Dialogfeld die **Transport** zu **Remote (nativ ohne Authentifizierung)**.  
  
9. Ändern der **Qualifizierer** auf den Namen des Computers (Hinweis: ein Verlauf der Einträge, vorhanden ist, sodass Sie diesen Namen nur einmal eingeben müssen).  
  
10. In der **verfügbare Prozesse** wählen Sie die Instanz von Ihr DE, die ausgeführt wird, und klicken Sie auf die **Anfügen** Schaltfläche.  
  
11. Nachdem die Symbole in Ihre DE geladen haben, fügen Sie Haltepunkte in Ihrem Code DE.  
  
12. Jedes Mal, wenn Sie zu beenden und neu starten des Debugvorgangs zur Verfügung, wiederholen Sie die Schritte 6 bis 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debuggen eines benutzerdefinierten Projekttyps  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in den normalen Registrierungsstruktur und die Auslastung geben Sie Ihr Projekt Projekt (Dies ist die Quelle, die Art Ihres Projekts, keine Instanziierung von der Art Ihres Projekts).  
  
2.  Öffnen Sie die Projekteigenschaften, und wechseln Sie zu der **Debuggen** Seite. Für die **Befehl**, geben Sie den Pfad zu der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (Standardmäßig ist dies *[Laufwerk]* \Programme\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Für die **Befehlsargumente**, Typ `/rootsuffix exp` für die experimentelle Registrierungsstruktur (erstellt als VSIP installiert wurde).  
  
4.  Klicken Sie auf **OK** um die Änderungen zu übernehmen.  
  
5.  Starten Sie Ihren Projekttyp durch Drücken von F5. Hierdurch wird eine zweite Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
6.  An diesem Punkt können Sie Haltepunkte in Ihrem Projekt Typ Quellcode platzieren.  
  
7.  In der zweiten Instanz des [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], laden oder erstellen Sie eine neue Instanz der Art Ihres Projekts. Während der laden oder erstellen können die festgelegten Haltepunkte anzusteuern sein.  
  
8.  Debuggen Sie Ihren Projekttyp.  
  
9. Wenn Sie den Prozess starten einer bereitgestellten Kompatibilitätsrichtlinie debuggen möchten, können Sie die Schritte ausführen, in der Prozedur "Debuggen einer benutzerdefinierten Debug-Engine" Verbindung mit Ihrem DE, nachdem es gestartet wird. Dadurch können Sie drei Instanzen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ausgeführt wird: eine für Ihr Projekt die Quelle, einen zweiten für Ihren Projekttyp der instanziierten, und klicken Sie auf eine dritte auf Ihre DE angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
