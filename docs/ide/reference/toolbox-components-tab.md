---
title: Toolbox, Registerkarte „Komponenten“
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a05ea5b06e985a21fbe45882ccfb36bfe194034
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947949"
---
# <a name="toolbox-components-tab"></a>Toolbox, Registerkarte „Komponenten“

Zeigt die Komponenten an, die Sie zu Visual Basic- und C#-Designern hinzufügen können. Zusätzlich zu den .NET Framework-Komponenten, die in Visual Studio enthalten sind (z.B. die Komponenten <xref:System.Messaging.MessageQueue> und <xref:System.Diagnostics.EventLog>), können Sie eigene Komponenten oder Drittanbieterkomponenten zu dieser Registerkarte hinzufügen.

 Wählen Sie im Menü **Ansicht** die Option **Toolbox**, um diese Registerkarte anzuzeigen. Wählen Sie in der **Toolbox** die Registerkarte **Komponenten**.

 **BackgroundWorker**

 Erstellt eine `System.ComponentModel.BackgroundWorker`-Komponenteninstanz, die einen Vorgang auf einem separaten, dedizierten Thread ausführen kann.

 **DirectoryEntry**

 Erstellt eine <xref:System.DirectoryServices.DirectoryEntry>-Komponenteninstanz, die einen Knoten oder ein Objekt in der Active Directory-Hierarchie kapselt und für die Interaktion mit Active Directory-Dienstanbietern verwendet werden kann.

 **DirectorySearcher**

 Erstellt eine <xref:System.DirectoryServices.DirectorySearcher>-Komponenteninstanz, mit der Sie Active Directory-Abfragen durchführen können.

 **ErrorProvider**

 Erstellt eine `System.Windows.Forms.ErrorProvider`-Komponenteninstanz, die dem Endbenutzer anzeigt, dass für ein Steuerelement auf einem Formular ein Fehler vorliegt.

 **EventLog**

 Erstellt eine <xref:System.Diagnostics.EventLog>-Komponenteninstanz, mit der sie mit nativen und benutzerdefinierten Ereignisprotokollen interagieren und unter anderem Ereignisse in ein Protokoll schreiben und Protokolldaten lesen können.

 **FileSystemWatcher**

 Erstellt eine <xref:System.IO.FileSystemWatcher>-Komponenteninstanz, mit der Sie Verzeichnisse oder Dateien, auf die Sie Zugriff haben, auf Veränderungen überwachen können.

 **HelpProvider**

 Erstellt eine `System.Windows.Forms.HelpProvider`-Komponenteninstanz, die Popup- oder Onlinehilfe für Steuerelemente bereitstellt.

 **ImageList**

 Erstellt eine `System.Windows.Forms.ImageList`-Komponenteninstanz, die Methoden zur Verwaltung einer Auflistung von `System.Drawing.Image`-Objekten bereitstellt.

 **MessageQueue**

 Erstellt eine <xref:System.Messaging.MessageQueue>-Komponenteninstanz, mit der Sie mit Meldungswarteschlangen interagieren und unter anderem Nachrichten von Warteschlangen lesen und an diese schreiben, Transaktionen verarbeiten und Verwaltungsaufgaben für die Warteschlange ausführen können.

 **PerformanceCounter**

 Erstellt eine <xref:System.Diagnostics.PerformanceCounter>-Komponenteninstanz, mit der sie mit Windows-Leistungsindikatoren interagieren und unter anderem neue Kategorien und Instanzen erstellen, Werte von Leistungsindikatoren lesen und Berechnungen zu Indikatorendaten durchführen können.

 **Process**

 Erstellt eine <xref:System.Diagnostics.Process>-Komponenteninstanz, mit der Sie die Daten von Prozessen auf Ihrem System beenden, starten und bearbeiten können.

 **SerialPort**

 Erstellt eine `System.IO.Ports.SerialPort`-Komponenteninstanz, die synchrone und ereignisgesteuerte E/A-Vorgänge, Zugriff auf Pin- und Unterbrechungszustände sowie Zugriff auf die Treibereigenschaften für den seriellen Anschluss bietet.

 **ServiceController**

 Erstellt eine <xref:System.ServiceProcess.ServiceController>-Komponenteninstanz, mit der Sie vorhandene Dienste bearbeiten und unter anderem Dienste starten und beenden sowie Befehle an sie senden können.

 **Zeitgeber**

 Erstellt eine <xref:System.Windows.Forms.Timer>-Komponenteninstanz, mit der Sie zeitbasierte Funktionen zu Ihren Windows-basierten Anwendungen hinzufügen können. Weitere Informationen finden Sie unter [Timer Component (Timer-Komponente)](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Es gibt auch eine systembasierte <xref:System.Timers.Timer>, die Sie zur **Toolbox** hinzufügen können. Diese <xref:System.Timers.Timer> ist für Serveranwendungen optimiert, und die <xref:System.Windows.Forms.Timer> eignet sich am besten für die Verwendung in Windows Forms.


## <a name="see-also"></a>Siehe auch

- [Programmieren mit Komponenten](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
- [Exemplarische Vorgehensweisen für die Komponentenprogrammierung](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)
- [Werkzeugkasten](../../ide/reference/toolbox.md)