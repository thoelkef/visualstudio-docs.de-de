---
title: Editorfactorys | Microsoft-Dokumentation
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
ms.openlocfilehash: fbf30d1fdb4fcce1e28a3c10c9949f1a11eae529
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58957717"
---
# <a name="editor-factories"></a>Editorfactorys
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Editor-Factory-Editor-Objekte erstellt und speichert sie in einen Fensterrahmen, der als eine physische Darstellung bezeichnet. Erstellt die Dokumentdaten und dokumentenansichtsobjekten, die zum Erstellen von Editoren und Designer erforderlich sind. Eine Editor-Factory ist erforderlich, um die Visual Studio-Kern-Editor und einem standard-Editor zu erstellen. Ein benutzerdefinierter Editor kann optional auch mit einer Editor-Factory erstellt werden.  
  
 Erstellen Sie eine Editorfactory, durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle. Das folgende Beispiel veranschaulicht, wie Sie implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> eine Editor-Factory zu erstellen:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Ein Editor wird beim ersten, die Sie, einen Dateityp, die vom Editor behandelt öffnen geladen. Sie können auswählen, um entweder einen bestimmten Editor oder der Standard-Editor zu öffnen. Wenn Sie die Standard-Editor auswählen, wird die integrierte Entwicklungsumgebung (IDE) bestimmt den richtigen-Editor zu öffnen, und klicken Sie dann geöffnet. Weitere Informationen finden Sie unter [ermitteln welcher Editor öffnet eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrierung-Editor-Factorys  
 Bevor Sie einen Editor verwenden können, den Sie erstellt haben, müssen Sie zunächst registrieren Informationen, einschließlich der Dateierweiterungen, die er verarbeiten kann.  
  
 Wenn Ihr VSPackage in verwaltetem Code geschrieben ist, können Sie die Managed Package Framework (MPF)-Methode <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> die Editor-Factory zu registrieren, nachdem das VSPackage geladen wurde. Wenn das VSPackage wird in nicht verwaltetem Code geschrieben, Sie müssen Ihre Editorfactory registrieren, indem die <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> Service.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrieren einer Editor-Factory mithilfe von verwaltetem Code  
 Müssen Sie Ihre Editorfactory in Ihre VSPackages Registrieren der `Initialize` Methode. Rufen Sie zuerst `base.Initialize`, und rufen dann <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> für jeden Editor-Factory  
  
 In verwaltetem Code besteht keine Notwendigkeit zum Aufheben der Registrierung einer Editor-Factory, da das VSPackage für Sie übernommen wird. Auch wenn der Editorfactory implementiert <xref:System.IDisposable>, sie automatisch freigegeben, wenn er nicht registriert ist.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registriert eine Editorfactory mit nicht verwaltetem code  
 In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung für das Editorpaket, verwenden die `QueryService` aufzurufende Methode `SVsRegisterEditors`. Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Methode durch die Implementierung der Übergabe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle. Sie müssen mplementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in einer separaten Klasse.  
  
## <a name="the-editor-factory-registration-process"></a>Der Prozess-Editor-Factory-Registrierung  
 Der folgende Prozess tritt beim Laden von Visual Studio als Editors mithilfe der Editorfactory:  
  
1.  Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt Systemaufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Diese Methode gibt die Editorfactory zurück. Visual Studio-Verzögerungen Laden der Paketdatei des Editors, jedoch erst ein Projektsystem tatsächlich Editor benötigt.  
  
3.  Wenn ein Projektsystem Editor benötigt, ruft Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, eine spezifische Methode, die sowohl das Dokument als auch die Dokumentenansicht Daten zurückgibt.  
  
4.  Wenn Aufrufe von Visual Studio-Editor-Factory mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> sowohl ein dokumentdatenobjekt und ein dokumentenansichtsobjekt zurückgeben, Visual Studio dann erstellt das Dokumentfenster, das dokumentenansichtsobjekt darin platziert und nimmt einen Eintrag in das Dokument ausgeführt Tabelle (RDT) für das dokumentendatenobjekt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Aktive Dokumenttabelle](../extensibility/internals/running-document-table.md)
