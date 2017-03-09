---
title: "Extension Analyzer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, Ladefehleranalyse"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Extension Analyzer
Der **Extension Analyzer** zeichnet die üblichsten Fehler beim Laden von Erweiterungen auf und protokolliert sie. Der **Extension Analyzer** wird in einem eigenen Toolfenster ausgeführt. Der Analyzer meldet die Ursache eines Fehlers und macht Vorschläge, wie dieser Fehler behoben werden kann.  
  
 Der [Extension Analyzer](http://go.microsoft.com/fwlink/?LinkId=205840) kann aus Visual Studio Gallery heruntergeladen werden. Die Assemblys des **Extension Analyzers** werden unter „\<*Visual Studio\-Installationspfad*\>\\Common7\\IDE\\PrivateAssemblies\\“ installiert.  
  
## Browser  
 Klicken Sie nach der Installation des **Extension Analyzers** im Menü **Extras** auf **Extension Analyzer** und anschließend auf **Browser**. Ein Fenster mit allen Erweiterungen wird angezeigt, die auf dem Computer registriert sind. Für VSIX\-Dateien, VSPackages, PkgDef\-Dateien und MEF\-Komponenten sind verschiedene Registerkarten verfügbar. Sie können die Listen nach jedem beliebigen Spaltennamen sortieren.  
  
1.  Die VSIX\-Registerkarte zeigt Informationen zu den installierten VSIX\-Erweiterungen an. Sie können Komponenten aufnehmen, indem Sie das Kontrollkästchen **Systemkomponenten anzeigen** aktivieren. Auf dieser Registerkarte können Sie zu den Protokolleinträgen für navigieren, das VSIX\-Manifest im XML\-Editor von Visual Studio öffnen und den Ordner öffnen, in dem die VSIX\-Erweiterung installiert ist.  
  
2.  Die Registerkarte „VSPackages“ zeigt Informationen zu den VSPackages an, die Visual Studio derzeit bekannt sind, unabhängig davon, ob diese geladen wurden. Diese Informationen umfassen den VSIX\-Bezeichner, die PKGDEF\-Datei und die GUID des VSPackage. Sie können System\-VSPackages aufnehmen, indem Sie das Kontrollkästchen **Show System Packages** \(Systempakete anzeigen\) aktivieren. Auf dieser Registerkarte können Sie zu den Protokolleinträgen navigieren, die auf der Registerkarte „VSIX“ aufgelisteten Erweiterungen und die PKGDEF\-Datei auf der Registerkarte „PkgDef\-Dateien“ anzeigen und das VSPackage analysieren. Die Ergebnisse der Analyse werden im Bereich **Ausgabe** angezeigt.  
  
3.  Die Registerkarte „PkgDef\-Dateien“ zeigt Informationen über die PKGDEF\-Dateien für Erweiterungen, die Visual Studio bekannt sind. Diese Informationen beinhalten den VSIX\-Bezeichner und den Pfad der Erweiterung. Sie können zum Protokoll oder der VSIX\-Registerkarte navigieren und sich die PKGDEF\-Datei im Editor anzeigen lassen.  
  
4.  Die Registerkarte „MEF\-Komponenten“ zeigt Informationen über MEF\-Komponenten, die Visual Studio bekannt sind. Diese Informationen beinhalten den VSIX\-Bezeichner und den Installationspfad der Erweiterung. Sie können Komponenten aufnehmen, indem Sie das Kontrollkästchen **Systemkomponenten anzeigen** aktivieren. Sie können auch zu dem entsprechenden VSIX\-Eintrag, der PKGDEF\-Datei und dem Verzeichnis navigieren, in dem die Erweiterung installiert wurde.  
  
> [!WARNING]
>  Sie werden möglicherweise dazu aufgefordert, die Fusion\-Protokollierung zu aktivieren. Geben Sie dazu einen Speicherort für die Protokolldateien an. Bevor Sie fortfahren können, werden möglicherweise Sie dazu aufgefordert, alle Visual Studio\-Instanzen neu zu starten.  
  
## Protokollanzeige  
 Sie können die Protokollierungsnachrichten mit der **Erweiterungsprotokollanzeige** anzeigen, wenn Sie ein Projekt ausführen, für das die Protokollierung aktiviert wurde \(durch Hinzufügen von \/log zu den Befehlszeilenargumenten des Projekts\). Weitere Informationen finden Sie unter [\/Log](../ide/reference/log-devenv-exe.md). Das Fenster **Erweiterungsprotokollanzeige** zeigt das Datum, den Listener, den Eintragstyp \(Typ der Nachricht\), den Fehlertyp, Informationen zu Klasse bzw. Schnittstelle und die Nachricht an. Sie können die Informationen sortieren und filtern.  
  
## Häufige Probleme beim Laden der Erweiterung  
 Einige typische Gründe für Fehler beim Laden einer Erweiterung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sind:  
  
-   Probleme mit Abhängigkeiten Eine Erweiterung kann so bereitgestellt worden sein, dass die abhängigen Assemblys nicht gefunden werden können.  
  
-   Ausnahmen. Wenn ein VSPackage geladen wird, ruft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>\-Methode auf. Wenn diese Methode eine Ausnahme auslöst, schlägt das Laden des VSPackage fehl. Der beste Weg, dieses Problem zu isolieren, ist, den Code der SetSite\-Methode in Einzelschritten durchzugehen.  
  
-   Nicht ordnungsgemäße Registrierung. Stellen Sie sicher, dass die Erweiterung ordnungsgemäß signiert ist und dass das VSPackage mit dem richtigen öffentlichen Schlüssel registriert ist.  
  
## Siehe auch  
 [Verwalten von VSPackages](../extensibility/managing-vspackages.md)