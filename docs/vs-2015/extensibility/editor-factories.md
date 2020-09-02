---
title: Editorfactory | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197765"
---
# <a name="editor-factories"></a>Editor-Factorys
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Editorfactory erstellt Editor-Objekte und legt Sie in einem Fensterrahmen ab, der als physische Ansicht bezeichnet wird. Es werden die Dokument Daten und die Dokument Ansichts Objekte erstellt, die zum Erstellen von Editoren und Designern benötigt werden. Eine Editorfactory ist erforderlich, um den Visual Studio-Kern-Editor und einen beliebigen Standard-Editor zu erstellen. Ein benutzerdefinierter Editor kann optional auch mit einer Editorfactory erstellt werden.  
  
 Sie erstellen eine Editorfactory, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle implementieren. Im folgenden Beispiel wird veranschaulicht, wie implementiert wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , um eine Editorfactory zu erstellen:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Ein Editor wird geladen, wenn Sie zum ersten Mal einen Dateityp öffnen, der von diesem Editor verarbeitet wird. Sie können entweder einen bestimmten Editor oder den Standard Editor öffnen. Wenn Sie den Standard-Editor auswählen, bestimmt die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) den richtigen Editor, der geöffnet werden soll, und öffnet ihn dann. Weitere Informationen finden Sie unter [bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Editorfactory wird registriert  
 Bevor Sie einen von Ihnen erstellten Editor verwenden können, müssen Sie zunächst Informationen dazu registrieren, einschließlich der Dateierweiterungen, die er verarbeiten kann.  
  
 Wenn das VSPackage in verwaltetem Code geschrieben wurde, können Sie die Editorfactory mithilfe der Methode Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> registrieren, nachdem das VSPackage geladen wurde. Wenn das VSPackage in nicht verwaltetem Code geschrieben ist, müssen Sie die Editorfactory mit dem <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> Dienst registrieren.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrieren einer Editorfactory mithilfe von verwaltetem Code  
 Sie müssen die Editorfactory in der-Methode Ihres VSPackage registrieren `Initialize` . Zuerst `base.Initialize` wird aufgerufen, und anschließend wird <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> für jede Editorfactory aufgerufen.  
  
 In verwaltetem Code muss die Registrierung einer Editorfactory nicht aufgehoben werden, da das VSPackage dies für Sie übernimmt. Wenn die Editorfactory implementiert <xref:System.IDisposable> , wird Sie auch automatisch verworfen, wenn die Registrierung aufgehoben wird.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrieren einer Editorfactory mithilfe von nicht verwaltetem Code  
 Verwenden Sie in der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung für das Editor-Paket die- `QueryService` Methode, um aufzurufen `SVsRegisterEditors` . Dies gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Durch übergeben der-Implementierung der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Schnittstelle wird die-Methode aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> . Sie müssen mplementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in einer separaten Klasse durch tragen.  
  
## <a name="the-editor-factory-registration-process"></a>Der Editorfactory-Registrierungsprozess  
 Der folgende Vorgang tritt auf, wenn Visual Studio Ihren Editor mithilfe der Editorfactory lädt:  
  
1. Das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt System ruft auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Diese Methode gibt die Editorfactory zurück. Visual Studio verzögert das Laden des Editor-Pakets jedoch, bis ein Projekt System den Editor tatsächlich benötigt.  
  
3. Wenn ein Projekt System den Editor benötigt, ruft Visual Studio auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , eine spezialisierte Methode, die sowohl die Dokument Ansicht als auch die Dokument Datenobjekte zurückgibt.  
  
4. Wenn Aufrufe von Visual Studio an die Editorfactory mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> sowohl ein Dokument Datenobjekt als auch ein Dokument Ansichts Objekt zurückgeben, erstellt Visual Studio das Dokument Fenster, platziert das Dokument Ansichts Objekt darin und führt einen Eintrag in der ausgelaufenden dokumententabelle (RDT) für das Dokument Datenobjekt durch.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Aktive Dokumenttabelle](../extensibility/internals/running-document-table.md)
