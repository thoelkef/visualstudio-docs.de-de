---
title: "Designentscheidungen f&#252;r Datenquellen-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellen-Steuerelement [Visual Studio SDK] Designentscheidungen"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Designentscheidungen f&#252;r Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die folgenden Entwurfs betreffenden Entscheidungen sollten für Projekte betrachtet werden, sofern die Quellcodeverwaltung implementiert.  
  
## Sind Informationen freigegeben oder privat?  
 Die wichtigste entscheidung Entwurf zu erfüllen, können, welche Informationen teilbar sind und welche privat ist.  Beispielsweise wird die Liste der Dateien für das Projekt freigegeben, aber in dieser Liste von Dateien, können einige Benutzer vertrauliche Dateien verfügen.  Compilereinstellungen freigegeben, aber das Projekt Start im Allgemeinen ist privat.  Einstellungen sind rein entweder freigegeben, rein privat oder freigegeben mit einer Überschreibung.  Arbeiten mit Absicht werden private Elemente, z. B. Dateien von Projektmappen benutzeroptionen \(.suo\) nicht in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]überprüft.  Stellen Sie sicher, dass alle privaten Informationen in den privaten Dateien wie der SUO\-Datei zu speichern oder eine bestimmte private Datei, die Sie erstellen, z. B. eine .csproj.user\-Datei für eine .vbproj.user\-Datei für Visual C\# oder Visual Basic aus.  
  
 Diese Entscheidung ist nicht Sammel und kann bei einem Element Element durch Seite gemacht werden.  
  
## Behandelt das Projekt Gerätedateien?  
 Eine andere wichtige entscheidung Entwurf, ob die Projektstruktur Gerätedateien verwendet.  Gerätedateien sind versteckte Dateien, die die Dateien, die zugrunde liegen im Projektmappen\-Explorer sichtbar und in den Dialogfeldern Einchecken\- und Auschecken.  Wenn Sie Gerätedateien verwenden, folgen Sie diesen Richtlinien:  
  
1.  Ordnen Sie Gerätedateien nicht mit dem Projektstamm Knoten\-dass ist, mit der Projektdatei selbst.  Die Projektdatei muss eine einzelne Datei sein.  
  
2.  Wenn Gerätedateien in einem Projekt hinzugefügt, entfernt oder umbenannt werden, müssen die entsprechenden Ereignisse <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> mit dem Flag festgelegt wurde ausgelöst werden, das die Dateien sind Gerätedateien angibt.  Diese Ereignisse werden von der Umgebung als Reaktion auf das Projekt aufgerufen, die die entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>\-Methoden aufgerufen werden.  
  
3.  Wenn das Projekt oder der Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> für eine Datei aufruft, werden die Gerätedateien, die dieser Datei zugeordnet sind, nicht automatisch ausgecheckt.  Führen Sie die Gerätedateien in zusammen mit der übergeordneten Datei.  Die Umgebung erkennt die Beziehung zwischen allen Dateien, die in Gerätedateien im Auschecken und die Benutzeroberfläche entsprechend auszublenden übergeben werden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Unterstützung von Datenquellen\-Steuerelement](../../extensibility/internals/supporting-source-control.md)