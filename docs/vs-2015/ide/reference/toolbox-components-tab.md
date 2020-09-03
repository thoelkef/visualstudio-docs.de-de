---
title: Toolbox, Registerkarte „Komponenten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661570"
---
# <a name="toolbox-components-tab"></a>Toolbox, Registerkarte „Komponenten“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt die Komponenten, die Sie zu [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]- und [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Designern hinzufügen können. Zusätzlich zu den Komponenten, die in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] enthalten sind [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , z. b. die <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> Komponenten und, können Sie auf dieser Registerkarte eigene Komponenten oder Komponenten von Drittanbietern hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Bearbeiten von Toolbox-Registerkarten](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Wählen Sie im Menü **Ansicht** die Option **Toolbox**, um diese Registerkarte anzuzeigen. Wählen Sie in der **Toolbox** die Registerkarte **Komponenten**.

 **BackgroundWorker** Erstellt eine `System.ComponentModel.BackgroundWorker` Komponenteninstanz, die einen Vorgang in einem separaten, dedizierten Thread ausführen kann.

 **Director-Eintrag** Erstellt eine <xref:System.DirectoryServices.DirectoryEntry> -Komponenteninstanz, die einen Knoten oder ein Objekt in der Active Directory Hierarchie kapselt und für die Interaktion mit Active Directory Dienstanbietern verwendet werden kann.

 **Directoriysearcher** Erstellt eine- <xref:System.DirectoryServices.DirectorySearcher> Komponenteninstanz, mit der Sie Abfragen für die Active Directory ausführen können.

 **ErrorProvider** Erstellt eine `System.Windows.Forms.ErrorProvider` Komponenteninstanz, die dem Endbenutzer angibt, dass einem Steuerelement in einem Formular ein Fehler zugeordnet ist.

 **Ereignisprotokoll** Erstellt eine- <xref:System.Diagnostics.EventLog> Komponenteninstanz, mit der Sie mit System-und benutzerdefinierten Ereignisprotokollen interagieren können, einschließlich Schreiben von Ereignissen in ein Protokoll und Lesen von Protokolldaten. Weitere Informationen finden Sie unter [Einführung in die EventLog-Komponente](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Erstellt eine- <xref:System.IO.FileSystemWatcher> Komponenteninstanz, mit der Sie Änderungen an allen Verzeichnissen oder Dateien überwachen können, auf die Sie Zugriff haben. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren von Instanzen von FileSystemWatcher-Komponenten](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Erstellt eine `System.Windows.Forms.HelpProvider` -Komponenteninstanz, die Popup-oder Online Hilfe für Steuerelemente bereitstellt.

 **ImageList** Erstellt eine- `System.Windows.Forms.ImageList` Komponenteninstanz, die Methoden zum Verwalten einer Auflistung von-Objekten bereitstellt `System.Drawing.Image` .

 **MessageQueue** Erstellt eine- <xref:System.Messaging.MessageQueue> Komponenteninstanz, mit der Sie mit Meldungs Warteschlangen interagieren können. Dies schließt das Lesen von Nachrichten aus und das Schreiben von Nachrichten in Warteschlangen, das Verarbeiten von Transaktionen und das Ausführen von Weitere Informationen finden Sie unter [Verwenden von Messagingkomponenten](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **Performance Counter** Erstellt eine- <xref:System.Diagnostics.PerformanceCounter> Komponenteninstanz, mit der Sie mit Windows-Leistungsindikatoren interagieren können, einschließlich der Erstellung neuer Kategorien und Instanzen, dem Lesen von Werten aus Indikatoren und der Durchführung von Berechnungen für Indikator Daten. Weitere Informationen finden Sie unter [Überwachen von Leistungsschwellenwerten](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Prozess** Erstellt eine <xref:System.Diagnostics.Process> Komponenteninstanz, die Sie verwenden können, um die den Prozessen in Ihrem System zugeordneten Daten zu starten, zu starten und zu bearbeiten. Weitere Informationen finden Sie unter [Monitoring and Managing Windows Processes (Überwachen und Verwalten von Windows-Prozessen)](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Erstellt eine `System.IO.Ports.SerialPort` -Komponenteninstanz, die synchrone und ereignisgesteuerte e/a-Vorgänge, Zugriff auf PIN-und Break-Zustände sowie Zugriff auf die Eigenschaften des seriellen Treibers bereitstellt.

 **ServiceController** Erstellt eine <xref:System.ServiceProcess.ServiceController> Komponenteninstanz, die Sie zum Bearbeiten vorhandener Dienste verwenden können, einschließlich starten und Beenden von Diensten und Senden von Befehlen an Sie. Weitere Informationen finden Sie unter [Monitoring Windows Services (Überwachen von Windows-Diensten)](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Timer** Erstellt eine- <xref:System.Windows.Forms.Timer> Komponenteninstanz, mit der Sie Ihren Windows-basierten Anwendungen zeitbasierte Funktionen hinzufügen können. Weitere Informationen finden Sie unter [Timer Component (Timer-Komponente)](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> Es gibt auch eine systembasierte <xref:System.Timers.Timer>, die Sie zur **Toolbox** hinzufügen können. Diese <xref:System.Timers.Timer> ist für Serveranwendungen optimiert, und die <xref:System.Windows.Forms.Timer> eignet sich am besten für die Verwendung in Windows Forms.

## <a name="see-also"></a>Weitere Informationen
 [Programmieren mit Komponenten](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) Komponenten [Programmierung](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) Exemplarische Vorgehensweisen [Toolbox](../../ide/reference/toolbox.md) [Elemente auswählen (Dialog Feld) (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
