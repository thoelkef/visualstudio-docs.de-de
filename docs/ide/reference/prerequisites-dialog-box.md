---
title: "Dialogfeld „Erforderliche Komponenten“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2e88e3999bdca7b926042685ca7bd2d561c12d5d
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box

In diesem Dialogfeld wird angegeben, welche erforderlichen Komponenten installiert werden, wie die Installation ausgeführt wird, und in welcher Reihenfolge die Pakete installiert werden.

Wählen Sie zum Aufrufen des Dialogfelds im **Projektmappen-Explorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen** . Klicken Sie auf der Seite **Veröffentlichen** auf **Erforderliche Komponenten**. Klicken Sie bei Setupprojekten im Menü **Projekt** auf **Eigenschaften**. Wenn das Dialogfeld **Eigenschaftenseiten** angezeigt wird, klicken Sie auf **Erforderliche Komponenten**.

## <a name="uielement-list"></a>UIElement-Liste

|Element|description|
|-------------|-----------------|
|**Setupprogramm zur Installation erforderlicher Komponenten erstellen**|Dies schließt die erforderlichen Komponenten im Setupprogramm (Setup.exe) der Anwendung ein, die je nach Abhängigkeit vor der Anwendung installiert werden. Diese Option ist standardmäßig ausgewählt. Wenn die Option nicht ausgewählt wurde, wird keine Setup.exe erstellt.|
|**Auswählen der für die Installation erforderlichen Komponenten**|Gibt an, ob Komponenten wie z. B. [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], Crystal Reports, usw. installiert werden.<br /><br /> Indem Sie im Kontrollkästchen neben **SQL Server 2005 Express Edition SP2** ein Häkchen setzen, legen Sie z.B. fest, dass vom Setupprogramm überprüft wird, ob diese Komponente auf dem Zielcomputer installiert ist. Außerdem installiert es die Komponente, wenn diese noch nicht vorhanden ist.<br /><br /> Ausführliche Informationen über die einzelnen erforderlichen Pakete finden Sie in der Tabelle mit Informationen zu den erforderlichen Komponenten weiter unten in diesem Thema.|
|**Microsoft Update auf weitere verteilbare Komponenten überprüfen**|Mithilfe dieses Links gelangen Sie auf die Website [Bootstrapperpakete zur Bereitstellung von Komponenten](http://go.microsoft.com/fwlink/?LinkId=208835), um nach Updates zu suchen.|
|**Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**|Dies gibt an, dass die erforderlichen Komponenten von der Website des Herstellers installiert werden müssen. Dies ist die Standardoption.|
|**Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**|Dies gibt an, dass die erforderlichen Komponenten vom gleichen Speicherort wie die Anwendung installiert werden müssen. Dadurch werden alle erforderlichen Pakete an den Speicherort für die Veröffentlichung kopiert. Damit diese Option funktioniert, müssen sich die erforderlichen Pakete auf dem Entwicklungscomputer befinden.|
|**Erforderliche Komponenten von folgendem Speicherort herunterladen**|Dies gibt an, dass die erforderlichen Komponenten vom ausgewählten Speicherort aus installiert werden müssen. Mithilfe der Schaltfläche **Durchsuche**n können Sie einen Speicherort auswählen.|

## <a name="prerequisites-information"></a>Informationen über erforderliche Komponenten

Die im Dialogfeld **Erforderliche Komponenten** aufgeführten erforderlichen Komponenten können von den in der folgenden Liste genannten abweichen. Die im Dialogfeld **Erforderliche Komponenten** aufgelisteten Pakete mit erforderlichen Komponenten werden automatisch festgelegt, wenn Sie das Dialogfeld zum ersten Mal öffnen. Wenn im Nachhinein Änderungen am Zielframework des Projekts vorgenommen werden, müssen die erforderlichen Komponenten manuell ausgewählt werden, um dem neuen Zielframework zu entsprechen.

|Element|description|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Mit diesem Paket wird Folgendes installiert:<br /><br /> – .NET Framework-Versionen 2.0, 3.0 und 3.5.<br />– Unterstützung für alle .NET Framework-Versionen auf 32-Bit- und 64-Bit-Betriebssystemen (x86 und x64).<br />– Sprachpakete für jede .NET Framework-Version, die mit dem Paket installiert wird.<br />– Service Packs für .NET Framework 2.0 und 3.0.<br /><br /> .NET Framework 3.0 ist im Lieferumfang von Windows Vista enthalten, und .NET Framework 3.5 ist in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthalten. .NET Framework 3.5 ist für alle Visual Basic- und Visual C#-Projekte erforderlich, die explizit für 32-Bit-Betriebssysteme kompiliert werden und für die das Zielframework auf **.NET Framework 3.5** festgelegt ist sowie für alle Visual Basic- und Visual C#-Projekte, die für 64-Bit-Betriebssysteme kompiliert werden. (IA64 wird nicht unterstützt) Beachten Sie, dass Visual Basic-Projekte und Visual C#-Projekte standardmäßig für jede CPU-Architektur kompiliert sind. Weitere Informationen finden Sie unter [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Verteilen von .NET Framework mit Ihrer Anwendung](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) und [Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Dieses Element ist standardmäßig ausgewählt.|
|**Microsoft .NET Framework 4.x**|Mit dem Paket wird .NET Framework 4 sowohl für die x86- als auch die x64-Plattform installiert.|
|**Microsoft-System-CLR-Typen für SQL Server 2014 (x64 und x86)**|Mit diesem Paket werden Microsoft-System-CLR-Typen für SQL Server 2014 für x64 oder x86 installiert.|
|**SQL Server 2008 R2 Express**|Mit diesem Paket wird Microsoft SQL Server 2008 R2 Express, eine kostenlose Edition von Microsoft SQL Server 2008 R2 installiert. Dies ist eine ideale Datenbank für kleine Web-, Server- oder Desktopanwendungen. Es kann kostenlos für Entwicklung und Produktion verwendet werden. Für das Verteilen von SQL Server 2008 R2 Express mit der Anwendung ist eine kostenlose [Registrierung](http://go.microsoft.com/fwlink/?LinkId=130380) erforderlich.|
|**SQL Server 2012 Express**|Mit diesem Paket wird Microsoft SQL Server 2012 Express installiert.|
|**SQL Server 2012 Express LocalDB**|Mit diesem Paket wird Microsoft SQL Server 2012 Express LocalDB installiert.|
|**Visual C++ "14"-Laufzeitbibliotheken (ARM)**|Mit diesem Paket wird die Visual C++-Laufzeitbibliotheken für die Itanium-Architektur, die die Routinen für die Programmierung für das Betriebssystem Microsoft Windows bereitstellen, installiert. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die in den Programmiersprachen C und C++ nicht enthalten sind.<br /><br /> Weitere Informationen finden Sie unter [C-Laufzeitbibliotheksreferenz](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14"-Laufzeitbibliotheken (x64)**|Mit diesem Paket werden die Visual C++-Laufzeitbibliotheken für x64-Betriebssysteme, die die Routinen für die Programmierung für das Betriebssystem Microsoft Windows bereitstellen, installiert. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die in den Programmiersprachen C und C++ nicht enthalten sind.<br /><br /> Weitere Informationen finden Sie unter [C-Laufzeitbibliotheksreferenz](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14"-Laufzeitbibliotheken (x86)**|Mit diesem Paket werden die Visual C++-Laufzeitbibliotheken für x86-Betriebssysteme, die die Routinen für die Programmierung für das Betriebssystem Microsoft Windows bereitstellen, installiert. Diese Routinen automatisieren viele allgemeine Programmieraufgaben, die in den Programmiersprachen C und C++ nicht enthalten sind.<br /><br /> Weitere Informationen finden Sie unter [C-Laufzeitbibliotheksreferenz](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Siehe auch

[Seite „Veröffentlichen“, Projekt-Designer](../../ide/reference/publish-page-project-designer.md)  
[Vorbedingungen für die Anwendungsbereitstellung](../../deployment/application-deployment-prerequisites.md)  
[Verteilen des .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)  
[Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen](../../deployment/deploying-prerequisites-for-64-bit-applications.md)  
[Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)
