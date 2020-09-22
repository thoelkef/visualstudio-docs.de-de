---
title: 'Vorgehensweise: Debuggen einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation'
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
ms.openlocfilehash: b7e710cec4536a5a1327580e56c60cb23ca36f4c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "90840975"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Gewusst wie: Debuggen einer benutzerdefinierten Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit einem Projekttyp wird die Debug-Engine (de) aus der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Methode gestartet. Dies bedeutet, dass die de unter dem Steuerelement der Instanz von gestartet wird, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die den Projekttyp steuert. Diese Instanz von kann jedoch [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nicht debuggen. Im folgenden werden die Schritte beschrieben, mit denen Sie Ihre benutzerdefinierte de Debuggen können.  
  
> [!NOTE]
> : Im Verfahren "Debuggen einer benutzerdefinierten Debug-Engine" müssen Sie warten, bis der de gestartet wird, bevor Sie ihn anfügen können. Wenn Sie ein Meldungs Feld am Anfang ihrer de platzieren, das beim Starten von de angezeigt wird, können Sie an diesem Punkt anfügen und dann das Meldungs Feld löschen, um den Vorgang fortzusetzen. Auf diese Weise können Sie alle de-Ereignisse abfangen.  
  
> [!WARNING]
> Sie müssen Remote Debugging installiert haben, bevor Sie die folgenden Verfahren ausführen. Weitere Informationen finden Sie unter [Remote Debuggen](../../debugger/remote-debugging.md) .  
  
### <a name="debugging-a-custom-debug-engine"></a>Debug-Engine  
  
1. Starten Sie msvsmon.exe, den Remotedebugmonitor.  
  
2. Wählen Sie **im Menü Extras** in msvsmon.exe die **Option Optionen** aus, um das Dialogfeld **Optionen** zu öffnen.  
  
3. Wählen Sie die Option "keine Authentifizierung" aus, und klicken Sie auf **OK**.  
  
4. Starten Sie eine Instanz von, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und öffnen Sie das benutzerdefinierte de-Projekt.  
  
5. Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , und öffnen Sie das benutzerdefinierte Projekt, das de startet (für die Entwicklung ist dies in der Regel in der experimentellen Registrierungs Struktur, die bei der Installation von VSIP eingerichtet ist).  
  
6. Laden Sie in dieser zweiten Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eine Quelldatei aus Ihrem benutzerdefinierten Projekt, und starten Sie das Programm, das gedeppt werden soll. Warten Sie einen Moment, bis der de geladen werden kann, oder warten Sie, bis ein Haltepunkt gedrückt wird.  
  
7. Wählen Sie in der ersten Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (mit Ihrem de-Projekt) im Menü **Debuggen** die Option **an den Prozess anhängen** aus.  
  
8. Ändern Sie im Dialogfeld **an den Prozess anhängen** den **Transport** in **Remote (nur System eigen ohne Authentifizierung)**.  
  
9. Ändern Sie den **Qualifizierer** in den Namen Ihres Computers (Hinweis: Es gibt einen Verlauf von Einträgen, sodass Sie diesen Namen nur einmal eingeben müssen).  
  
10. Wählen Sie in der Liste **Verfügbare Prozesse** die Instanz von aus, die ausgeführt wird, und klicken Sie auf die Schaltfläche **Anfügen** .  
  
11. Platzieren Sie nach dem Laden der Symbole in ihren de-Code Breakpoints.  
  
12. Wenn Sie den Debugprozess abbrechen und dann neu starten, wiederholen Sie die Schritte 6 bis 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debuggen eines benutzerdefinierten Projekt Typs  
  
1. Starten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Sie in der normalen Registrierungs Struktur, und laden Sie das Projekttyp Projekt (also die Quelle in ihren Projekttyp, keine Instanziierung des Projekt Typs).  
  
2. Öffnen Sie die Projekteigenschaften, und wechseln Sie zur Seite **Debuggen** . Geben Sie für den **Befehl**den Pfad zur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE ein (Standardmäßig ist dies *[Laufwerk]* \Programme\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Geben Sie für die **Befehlsargumente** `/rootsuffix exp` für die experimentelle Registrierungs Struktur ein (bei der Installation von VSIP erstellt).  
  
4. Klicken Sie auf **OK** , um die Änderungen zu übernehmen.  
  
5. Starten Sie den Projekttyp durch Drücken von F5. Dadurch wird eine zweite Instanz von gestartet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
6. An diesem Punkt können Sie Haltepunkte in ihren Projekttyp-Quellcode platzieren.  
  
7. Laden Sie in der zweiten Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eine neue Instanz des Projekt Typs, oder erstellen Sie Sie. Während der Auslastung oder Erstellung werden die Breakpoints möglicherweise gedrückt.  
  
8. Debuggen des Projekt Typs.  
  
9. Wenn Sie das Starten eines de-Vorgangs debuggen möchten, können Sie die Schritte im Verfahren "Debuggen einer benutzerdefinierten Debug-Engine" ausführen, um Sie nach dem Start an Ihre de anzufügen. Dadurch erhalten Sie drei Instanzen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , die ausgeführt werden: eine für die Projekttyp Quelle, eine Sekunde für den instanziierten Projekttyp und ein drittes, das an Ihren de angeschlossen ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
