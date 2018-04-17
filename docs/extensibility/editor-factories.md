---
title: Editor-Factorys | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="editor-factories"></a>Editor-Factorys
Eine Editorfactory-Editor-Objekte erstellt und schreibt sie in einen Fensterrahmen als physische Sicht bezeichnet. Erstellt die Dokumentdaten und Ansicht Document-Objekte, die zum Erstellen von Editoren und Designern erforderlich sind. Eine Editorfactory ist erforderlich, um die Visual Studio-Core-Editor und alle standard-Editors zu erstellen. Ein benutzerdefinierter Editor kann optional auch eine Editor-Factory erstellt werden.  
  
 Erstellen Sie eine Editorfactory durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle. Im folgende Beispiel wird veranschaulicht, wie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> eine Editorfactory zu erstellen:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Ein Editor wird beim ersten, die Sie einen Dateityp behandelt, die von diesem Editor öffnen geladen. Sie können auswählen, um einen bestimmten Editor oder Standard-Editor zu öffnen. Wenn Sie die Standard-Editor auswählen, wird der integrierten Entwicklungsumgebung (IDE) bestimmt den richtigen-Editor zu öffnen und anschließend geöffnet. Weitere Informationen finden Sie unter [bestimmen den Editor öffnet eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrierung-Editor-Factorys  
 Bevor Sie einen Editor verwenden können, den Sie erstellt haben, müssen Sie zuerst registrieren Informationen, einschließlich der Dateierweiterungen, die sie behandeln kann.  
  
 Wenn Ihr VSPackage in verwaltetem Code geschrieben ist, können Sie die Managed Package Framework (MPF) Methode <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> die Editor-Factory zu registrieren, nachdem Ihr VSPackage geladen wurde. Wenn Ihr VSPackage in nicht verwaltetem Code geschrieben wird, müssen Sie die Editorfactory registrieren, indem die <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> Dienst.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrieren eine Editor-Factory mithilfe von verwaltetem Code  
 Sie müssen Ihre Editorfactory in Ihr VSPackages Registrieren der `Initialize` Methode. Rufen Sie zuerst `base.Initialize`, und rufen dann <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> für jede Factory-Editors  
  
 In verwaltetem Code besteht keine Notwendigkeit zum Aufheben der Registrierung einer Editorfactory, da das VSPackage dies für Sie ausführt. Auch wenn die Editorfactory implementiert <xref:System.IDisposable>, sie automatisch freigegeben, wenn es nicht registriert ist.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrieren eine Editorfactory mit nicht verwaltetem code  
 In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung für das Editorpaket, verwenden die `QueryService` aufzurufende `SVsRegisterEditors`. Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Methode Ihre Implementierung übergeben, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle. Sie müssen Mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in einer separaten Klasse.  
  
## <a name="the-editor-factory-registration-process"></a>Der Prozess-Editor-Factory-Registrierung  
 Der folgende Prozess tritt beim Laden von Visual Studio Ihrem-Editors mithilfe der Editorfactory:  
  
1.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt Systemaufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Diese Methode gibt die Editor-Factory. Visual Studio-Verzögerungen Laden der Paketdatei des Editors, jedoch erst ein Projektsystem Editor tatsächlich benötigt.  
  
3.  Wenn ein Projektsystem Editor benötigt wird, ruft Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, eine spezielle Methode, die Dokumentansicht und das Dokument Datenobjekte zurückgibt.  
  
4.  Wenn Visual Studio dem Editor-Factory mit anruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ein dokumentdatenobjekt und ein Document-Objekt zurückgeben, Visual Studio dann erstellt das Dokumentfenster, des dokumentansichtsobjekts darin platziert und stellt einen Eintrag in das Dokument ausgeführt Tabelle (RDT) für das Dokument-Datenobjekt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Aktive Dokumenttabelle](../extensibility/internals/running-document-table.md)