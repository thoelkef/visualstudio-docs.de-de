---
title: "Einf&#252;hrung in internationale Anwendungen basierend auf .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ASP.NET, Globalisierung"
  - "Assembly-Ressourcendateivorlage"
  - "Kultur, Festlegen"
  - "Fallbackressourcen"
  - "Globalisierung [Visual Studio], Kultureinstellung"
  - "Globalisierung [Visual Studio], Internationale Anwendungen"
  - "Internationale Anwendungen [Visual Studio], Informationen über internationale Anwendungen"
  - "Lokalisierung [Visual Studio], .NET-Lokalisierungsmodell"
  - "Lokalisierung [Visual Studio], Kultureinstellung"
  - "Ressourcendateien, Fallbackprozesse"
  - "Ressourcen [Visual Studio], Fallbacksystem"
  - "Ressourcen [Visual Studio], Lokalisierung"
  - "Zeichenfolgen [Visual Studio], Lokalisieren"
  - "Benutzeroberfläche, Kultureinstellung"
  - "Webanwendungen [.NET Framework], Globalisierung"
  - "Windows Forms, Globalisierung"
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Einf&#252;hrung in internationale Anwendungen basierend auf .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verfügt über zwei Bestandteile zur Erstellung von Anwendungen, die weltweit einsetzbar sind: Globalisierung und Lokalisierung. Globalisierung bezeichnet dabei den Prozess des Entwerfens von Anwendungen, die kulturspezifisch angepasst werden können, und Lokalisierung den Prozess der kulturspezifischen Übersetzung von Ressourcen.  Allgemeine Informationen über das Entwerfen von Anwendungen für mehrere Sprachen finden Sie unter [Empfehlungen für die Entwicklung weltweit einsatzfähiger Anwendungen](../Topic/Best%20Practices%20for%20Developing%20World-Ready%20Applications.md).  
  
 Das [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Lokalisierungsmodell besteht aus einer Hauptassembly, die den Anwendungscode und die Reserveressourcen \(Zeichenfolgen, Bilder und andere Objekte für die Sprache, in der die Anwendung ursprünglich entwickelt wurde\) enthält.  Jede lokalisierte Anwendung verfügt über Satellitenassemblys oder Assemblys, die nur die lokalisierten Ressourcen enthalten.  Da sich die Sicherungsressourcen immer in der Hauptassembly befinden, versucht <xref:System.Resources.ResourceManager> Ressourcen, die nicht in der lokalisierten Satellitenassembly zu finden sind, durch hierarchisches Vorgehen zu laden und greift letztendlich auf die Ressourcen in der Hauptassembly zurück.  Ausführlichere Informationen über das Ressourcen\-Fallbacksystem finden Sie unter [Hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Eine empfehlenswerte Lokalisierungsressource ist das Glossar für alle lokalisierten Microsoft\-Produkte.  Diese CSV\-Datei enthält über 12.000 englische Begriffe und die Übersetzung der Begriffe in bis zu 59 verschiedene Sprachen.  Das Glossar steht auf der Webseite [Microsoft Terminology Translations](http://go.microsoft.com/fwlink/?LinkId=128146) zum Herunterladen zur Verfügung.  
  
 Das Projektsystem für Windows Forms\-Anwendungen kann sowohl für das Reservesystem als auch für alle gewünschten benutzeroberflächenspezifischen Kultureinstellungen Ressourcendateien generieren.  Die Reserveressourcendatei ist in die Hauptassembly integriert. Kulturspezifische Ressourcendateien werden in Satellitenassemblys integriert, wobei für jede benutzeroberflächenspezifische Kultureinstellung ein Assembly besteht.  Bei der Erstellung eines Projekts werden die Ressourcendateien über das XML\-Format von Visual Studio \(**.resx**\) in ein binäres Zwischenformat \(**.resources**\) kompiliert und anschließend in die Satellitenassemblys eingebettet.  
  
 Mit den Projektsystemen für Windows Forms und Web Forms können Sie mithilfe einer Vorlage Ressourcendateien erstellen, auf die Ressourcen zugreifen und das Projekt erstellen.  Die Satellitenassemblys werden zusammen mit der Hauptassembly erstellt.  
  
 Wenn eine lokalisierte Anwendung ausgeführt wird, wird das Erscheinungsbild durch die beiden Kulturwerte festgelegt.  \(Eine *Kultureinstellung* enthält verschiedene Benutzereinstellungsinformationen, die sich auf Sprache, Umgebung und kulturelle Konventionen des Benutzers beziehen.\) Die oberflächenspezifische Kultureinstellung legt fest, welche Ressourcen geladen werden.  Die oberflächenspezifische Kultur wird als `UICulture` in den Web.config\-Dateien und den Page\-Direktiven sowie im Visual Basic\- oder Visual C\#\-Code als <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> festgelegt.  Die Kultureinstellung legt die Formatierung von Werten, wie Daten, Zahlen, Währung, usw. fest.  Die Kultur wird als `Culture` in den Web.config\-Dateien und den Page\-Direktiven sowie im Visual Basic\- oder Visual C\#\-Code als <xref:System.Globalization.CultureInfo.CurrentCulture%2A> festgelegt.  
  
## Siehe auch  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)