---
title: Einführung in internationale Anwendungen basierend auf .NET Framework
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 773e6a2f351c0256fee17b1e07ff37fe9567198b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Einführung in internationale Anwendungen basierend auf .NET Framework

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist das Erstellen einer weltweit einsatzfähigen Anwendung zweiteilig: es besteht aus der Globalisierung, also dem Entwerfen einer Anwendung, die an unterschiedliche Kulturen angepasst werden kann, und aus der Lokalisierung, also dem Übersetzen von Ressourcen für eine bestimmte Kultur. Allgemeine Informationen zum Entwerfen von Anwendungen für ein internationales Publikum finden Sie unter [Empfehlungen für die Entwicklung weltweit einsatzfähiger Anwendungen](http://msdn.microsoft.com/Library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).

 Das Lokalisierungsmodell [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] besteht aus einer Hauptassembly, die sowohl den Anwendungscode als auch die Ausweichressourcen enthält, und aus anderen Objekten für die Sprache, in der die Anwendung ursprünglich entwickelt wurde. Jede lokalisierte Anwendung enthält Satellitenassemblys oder Assemblys, die nur die lokalisierten Ressourcen enthalten. Da das Hauptassembly immer die Ausweichressourcen enthält, versucht <xref:System.Resources.ResourceManager> diese in hierarchischer Reihenfolge zu laden, wenn eine Ressource nicht in der lokalisierten Satellitenassembly gefunden werden kann. Schließlich kehrt es wieder zur Ressource in der Hauptassembly zurück. Das Ausweichsystem für Ressourcen wird unter [Hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/hierarchical-organization-of-resources-for-localization.md) ausführlicher erklärt.

 Sie sollten in Erwägung ziehen, das Glossar für alle lokalisierten Microsoft-Produkte zu verwenden. Diese CSV-Datei enthält über 12.000 englische Begriffe mit den jeweiligen Übersetzungen in bis zu 59 verschiedenen Sprachen. Dieses Glossar steht unter [Microsoft Terminology Translations (Übersetzung von Microsoft-Terminologie)](http://go.microsoft.com/fwlink/?LinkId=128146) zum Download zu Verfügung.

 Das Projektsystem für Windows Forms-Anwendungen kann Ressourcendateien sowohl für die Ausweich- als auch für jede weitere Benutzeroberflächenkultur generieren. Die Ausweichressourcendatei ist in der Hauptassembly eingebaut, und die kulturspezifischen Ressourcendateien werden danach in die Satellitassembly eingebaut – jeweils eine pro Benutzeroberflächenkultur. Wenn Sie ein Projekt erstellen, werden die Ressourcendateien vom Visual Studio XML-Format (.resx) in ein binäres Zwischenformat (.resources) kompiliert. Anschließend werden sie in Satellitenassemblys eingebettet.

 Mit dem Projektsystem sowohl für Windows Forms als auch für Web Form können Sie Ressourcendateien mithilfe einer Assembly-Ressourcendateivorlage erstellen, auf die Ressourcen zugreifen und Ihre eigenen Projekte erstellen. Mit Erstellen des Hauptassemblys werden immer auch Satellitenassemblys erstellt.

 Das Aussehen einer lokalisierten Anwendung bei dessen Ausführung hängt von zwei Kulturwerten ab. (Eine *Kultur* setzt sich aus Informationen zu Benutzereinstellungen bezüglich der Sprache des Benutzers, dessen Umgebung und dessen kulturellen Konventionen zusammen.) Die Kultureinstellungen der Benutzeroberfläche legen fest, welche Ressourcen geladen werden. Die Benutzeroberflächenkultur ist in Dateien namens „Web.config“ und Seitenanweisungen auf `UICulture` festgelegt, und in Visual Basic- oder C#-Code auf <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>. Die Kultureinstellung bestimmt das Format von Werten wie z.B. Daten, Nummern, Währungen usw. Die Kultur ist in Dateien namens „Web.config“ und Seitenanweisungen auf `Culture` festgelegt, und in Visual Basic- oder C#-Code auf <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.

## <a name="see-also"></a>Siehe auch

- <xref:System.Globalization>
- <xref:System.Resources>
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
- [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)