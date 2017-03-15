---
title: "Einführung in internationale Anwendungen basierend auf .NET Framework | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 5d04af26004b5915fcd373fda154ac79816e475c
ms.lasthandoff: 02/22/2017

---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Einführung in internationale Anwendungen basierend auf .NET Framework
In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist das Erstellen einer weltweit einsatzfähigen Anwendung zweiteilig: es besteht aus der Globalisierung, also dem Entwerfen einer Anwendung, die an unterschiedliche Kulturen angepasst werden kann, und aus der Lokalisierung, also dem Übersetzen von Ressourcen für eine bestimmte Kultur. Allgemeine Informationen zum Entwerfen von Anwendungen für ein internationales Publikum finden Sie unter [Empfehlungen für die Entwicklung weltweit einsatzfähiger Anwendungen](http://msdn.microsoft.com/Library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 Das Lokalisierungsmodell [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] besteht aus einer Hauptassembly, die sowohl den Anwendungscode als auch die Ausweichressourcen enthält, und aus anderen Objekten für die Sprache, in der die Anwendung ursprünglich entwickelt wurde. Jede lokalisierte Anwendung enthält Satellitenassemblys oder Assemblys, die nur die lokalisierten Ressourcen enthalten. Da das Hauptassembly immer die Ausweichressourcen enthält, versucht <xref:System.Resources.ResourceManager> diese in hierarchischer Reihenfolge zu laden, wenn eine Ressource nicht in der lokalisierten Satellitenassembly gefunden werden kann; schließlich kehrt es wieder zur Ressource in der Hauptassembly zurück. Das Ausweichsystem für Ressourcen wird unter [Hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/hierarchical-organization-of-resources-for-localization.md) ausführlicher erklärt.  
  
 Sie sollten in Erwägung ziehen, das Glossar für alle lokalisierten Microsoft-Produkte zu verwenden. Diese CSV-Datei enthält über 12.000 englische Begriffe mit den jeweiligen Übersetzungen in bis zu 59 verschiedenen Sprachen. Dieses Glossar steht unter [Microsoft Terminology Translations (Übersetzung von Microsoft-Terminologie)](http://go.microsoft.com/fwlink/?LinkId=128146) zum Download zu Verfügung.  
  
 Das Projektsystem für Windows Forms-Anwendungen kann Ressourcendateien sowohl für die Ausweich- als auch für jede weitere Benutzeroberflächenkultur generieren. Die Ausweichressourcendatei ist in der Hauptassembly eingebaut, und die kulturspezifischen Ressourcendateien werden danach in die Satellitassembly eingebaut – jeweils eine pro Benutzeroberflächenkultur. Wenn Sie ein Projekt erstellen, werden die Ressourcendateien vom Visual Studio XML-Format (.resx) in ein binäres Zwischenformat (.resources) kompiliert. Anschließend werden sie in Satellitenassemblys eingebettet.  
  
 Mit dem Projektsystem sowohl für Windows Forms als auch für Web Form können Sie Ressourcendateien mithilfe einer Assembly-Ressourcendateivorlage erstellen, auf die Ressourcen zugreifen und Ihre eigenen Projekte erstellen. Mit Erstellen des Hauptassemblys werden immer auch Satellitenassemblys erstellt.  
  
 Das Aussehen einer lokalisierten Anwendung bei dessen Ausführung hängt von zwei Kulturwerten ab. (Eine *Kultur* setzt sich aus Informationen zu Benutzereinstellungen bezüglich der Sprache des Benutzers, dessen Umgebung und dessen kulturellen Konventionen zusammen.) Die Kultureinstellungen der Benutzeroberfläche legen fest, welche Ressourcen geladen werden. Die Kultur der Benutzeroberfläche ist auf `UICulture` in Web.config-Dateien und Seitendirektiven festgelegt, und auf <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> in Visual Basics oder Visual C#-Code. Die Kultureinstellung bestimmt das Format von Werten wie z.B. Daten, Nummern, Währungen usw. Die Kultur ist auf `Culture` in Web.config-Dateien und Seitendirektiven festgelegt, und auf <xref:System.Globalization.CultureInfo.CurrentCulture%2A> in Visual Basics oder Visual C#-Code.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)
