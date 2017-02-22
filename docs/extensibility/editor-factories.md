---
title: "Editor-Factorys | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - editorfactorys"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Editor-Factorys
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Editor factory Editor Objekte erstellt und setzt sie in einen Fensterrahmen, wird als eine physikalische Ansicht.  Erstellen Sie die Dokumentdaten der Dokumente und die Objekte, die erforderlich sind, um Editoren und Designer erstellen.  Eine Editor factory ist erforderlich, um den Visual Studio\-Kern Editor und jeden Standardwert des Editors zu erstellen.  Ein benutzerdefinierter Editor kann auch mit einem Editor factory optional erstellt werden.  
  
 Sie erstellen eine Editor factory, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>\-Schnittstelle implementieren.  Im folgenden Beispiel wird veranschaulicht, wie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implementiert, um eine Editor factory zu erstellen:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Ein Editor wird das erste Mal geladen, dem Sie einen Dateityp öffnen, die von diesem Editor behandelt wird.  Sie können entweder einen bestimmten Editor oder den Standard\-Editor geöffnet werden soll.  Wenn Sie den Standard\-Editor auswählen, bestimmt die integrierte Entwicklungsumgebung \(Integrated Development Environment, IDE\) die richtige Editor zu öffnenden und öffnet sie.  Weitere Informationen finden Sie unter [Bestimmen daraufhin\-Editor eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## Registrieren Editor\-Factorys  
 Bevor Sie einen Editor verwenden können, den Sie erstellt haben, müssen Sie Informationen über diese zunächst, einschließlich der Dateierweiterungen registrieren, die sie behandeln kann.  
  
 Wenn ein VSPackage in verwaltetem Code geschrieben wird, können Sie die Methode <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> verwenden \(MPF\) des verwalteten Paketframeworks der Editor factory zu registrieren, nachdem VSPackages geladen wurde.  Wenn ein VSPackage in nicht verwaltetem Code geschrieben wird, müssen Sie den Editor factory registrieren, indem Sie den <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> Dienst verwenden.  
  
### Eine Editor\-Factory mithilfe von verwaltetem Code registrieren  
 Sie müssen den Editor factory VSPackages in der `Initialize`\-Methode registriert werden.  Erster Aufruf `base.Initialize`, und rufen Sie dann <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> für jede Editor an factory  
  
 In verwaltetem Code besteht keine Notwendigkeit, eine Editor factory Registrierung aufgehoben, da ein VSPackage dies für Sie verarbeitet.  Auch wenn der Editor factory <xref:System.IDisposable>implementiert, wird es automatisch freigegeben, wenn sich deren Registrierung aufgehoben werden soll.  
  
### Eine Editor factory mithilfe von nicht verwaltetem Code registrieren  
 In der Implementierung für das Paket <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Editor, verwenden Sie die `QueryService`\-Methode, um `SVsRegisterEditors`aufzurufen.  Das zu, gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>zurück.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>\-Methode an, indem Sie die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>\-Schnittstelle übergeben.  Sie müssen mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in einer separaten Klasse.  
  
## Der Editor\-Factory\-Anmeldeprozess  
 Der folgende Prozess tritt auf, wenn Visual Studio den Editor mithilfe der Editor factorys wird:  
  
1.  Das Projektsystem ruft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>an.  
  
2.  Diese Methode gibt den Editor factory zurück.  Visual Studio verzögert, das Paket des Editors zu laden, jedoch, bis ein Projektsystem erforderlich sind tatsächlich den Editor.  
  
3.  Wenn ein Projektsystem den Editor erfordert, ruft Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, eine spezielle Methode auf, wenn sie beide Dokumente und die Ansicht das Dokument datenobjekte zurückgibt.  
  
4.  Wenn Aufrufe von Visual Studio factory Editor mithilfe des <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ein Dokument das angegebene Channeldatenobjekt und die Dokumente ein Objekt zurückgeben, erstellt Visual Studio dann das Dokumentfenster, das Dokument platziert dort die Objekt und wandelt einen Eintrag in die Dokumente \(Drehtransformator\) für das Dokument das angegebene Channeldatenobjekt.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Dokumenttabelle der ausgeführten](../extensibility/internals/running-document-table.md)