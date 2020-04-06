---
title: 'Gewusst wie: Debuggen einer benutzerdefinierten Debug-Engine | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738584"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Gewusst wie: Debuggen eines benutzerdefinierten Debugmoduls
Ein Projekttyp startet das Debugmodul (DE) von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Methode aus. Dies bedeutet, dass die DE unter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der Kontrolle der Instanz der Steuerung des Projekttyps gestartet wird. Diese Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kann die DE jedoch nicht debuggen. Im Folgenden sind die Schritte, mit denen Sie Ihre benutzerdefinierte DE debuggen können.

> [!NOTE]
> : Im Verfahren "Debug a custom debug engine" müssen Sie warten, bis die DE gestartet wird, bevor Sie sie anfügen können. Wenn Sie ein Meldungsfeld am Anfang Ihrer DE platzieren, das beim Start der DE angezeigt wird, können Sie an diesem Punkt anfügen und dann das Meldungsfeld löschen, um fortzufahren. Auf diese Weise können Sie alle DE-Ereignisse abfangen.

> [!WARNING]
> Sie müssen Remote-Debugging installiert haben, bevor Sie die folgenden Verfahren versuchen. Weitere Informationen finden Sie unter [Remote-Debugging.](../../debugger/remote-debugging.md)

## <a name="debug-a-custom-debug-engine"></a>Debuggen eines benutzerdefinierten Debugmoduls

1. Starten Sie *msvsmon.exe*, den Remote-Debugmonitor.

2. Wählen Sie im Menü **Extras** in *msvsmon.exe* **Optionen** aus, um das Dialogfeld **Optionen** zu öffnen.

3. Wählen Sie die Option "Keine Authentifizierung" und klicken Sie auf **OK**.

4. Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine Instanz von, und öffnen Sie Ihr benutzerdefiniertes DE-Projekt.

5. Starten Sie eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zweite Instanz von, und öffnen Sie Ihr benutzerdefiniertes Projekt, das die DE startet (für die Entwicklung ist dies in der Regel in der experimentellen Registrierungsstruktur, die eingerichtet wird, wenn VSIP installiert wird).

6. Laden Sie in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dieser zweiten Instanz eine Quelldatei aus Ihrem benutzerdefinierten Projekt, und starten Sie das zu debuggende Programm. Warten Sie einige Augenblicke, bis die DE geladen werden kann, oder warten Sie, bis ein Haltepunkt erreicht wird.

7. Wählen Sie in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der ersten Instanz (mit Ihrem DE-Projekt) im **Menü Debug** die Option **An Prozess anfügen** aus.

8. Ändern Sie im Dialogfeld **An Prozess anfügen** den **Transport** in **Remote (nur nativ ohne Authentifizierung)**.

9. Ändern Sie den **Qualifizierer** in den Namen Ihres Computers (Hinweis: Es gibt eine Historie von Einträgen, daher müssen Sie diesen Namen nur einmal eingeben).

10. Wählen Sie in der Liste **Verfügbare Prozesse** die Instanz Ihrer DE aus, die ausgeführt wird, und klicken Sie auf die Schaltfläche **Anfügen.**

11. Nachdem die Symbole in De geladen haben, platzieren Sie Haltepunkte in Ihrem DE-Code.

12. Wiederholen Sie jedes Mal, wenn Sie den Debugvorgang beenden und dann neu starten, die Schritte 6 bis 10.

## <a name="debug-a-custom-project-type"></a>Debuggen eines benutzerdefinierten Projekttyps

1. Beginnen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie in der normalen Registrierungsstruktur, und laden Sie das Projekttypprojekt (dies ist die Quelle für den Projekttyp, keine Instanziierung des Projekttyps).

2. Öffnen Sie die Project-Eigenschaften, und wechseln Sie zur **Seite Debuggen.** Geben **Command**Sie für den Befehl [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Pfad zur IDE ein (standardmäßig ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dies *[Laufwerk]*,,Programmdateien» ,,Microsoft 8'Common7'IDE'devenv.exe').

3. Geben Sie für `/rootsuffix exp` die **Befehlsargumente**ein, geben Sie für die experimentelle Registrierungsstruktur ein (erstellt, als VSIP installiert wurde).

4. Klicken Sie auf **OK** , um die Änderungen zu übernehmen.

5. Starten Sie Ihren Projekttyp, indem Sie **F5**drücken. Dadurch wird eine zweite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Instanz von gestartet.

6. An diesem Punkt können Sie Haltepunkte in Ihrem Projekttypquellcode platzieren.

7. Laden oder erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Sie in der zweiten Instanz von eine neue Instanz Ihres Projekttyps. Während der Last oder Erstellung können Ihre Haltepunkte getroffen werden.

8. Debuggen Sie Ihren Projekttyp.

9. Wenn Sie den Prozess zum Starten einer DE debuggen, können Sie die Schritte in der Prozedur "Debug a custom debug engine" ausführen, um sie nach dem Start an Ihre DE anzuhängen. Dadurch erhalten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] drei Instanzen der Ausführung: eine für Ihre Projekttypquelle, eine Zweite für Ihren instanziierten Projekttyp und eine dritte, die an Ihre DE angefügt ist.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)
