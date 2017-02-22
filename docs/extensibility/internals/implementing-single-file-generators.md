---
title: "Implementieren von Einzeldatei-Generatoren | Microsoft Docs"
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
  - "Implementieren von benutzerdefinierten tools"
  - "Projekte [Visual Studio SDK] Erweiterbarkeit"
  - "Projekte [Visual Studio SDK] verwaltet die benutzerdefinierten tools"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementieren von Einzeldatei-Generatoren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein benutzerdefiniertes Tool — manchmal als einem Einzeldatei\-Generator — kann verwendet werden, um die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projektsysteme in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zu erweitern.  Ein benutzerdefiniertes Tool ist eine COM\-Komponente, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>\-Schnittstelle implementiert.  Mithilfe dieser Schnittstelle umgewandelt Ein\-Input ein benutzerdefiniertes Tool eine Datei in eine Datei mit Ein\-Output.  Das Ergebnis der Transformation kann Quellcode oder eine beliebige andere Ausgabe, die hilfreich ist.  Zwei Beispiele für benutzerdefinierte Tool\-generierten Codedateien sind der Code, der in Reaktion auf Änderungen in einem visuellen Designer generiert werden und die Dateien, die mithilfe der Web Services Description Language \(WSDL\) generiert werden.  
  
 Wenn ein benutzerdefiniertes Tool geladen wird oder die Eingabedatei gespeichert wird, ruft das Projektsystem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>\-Methode auf und übergibt einen Verweis auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> Rückrufschnittstelle vom Tool, mit dem Benutzer den Status Gestartet melden kann.  
  
 Die Ausgabedatei, die das benutzerdefinierte Tool generiert, wird dem Projekt mit einer Abhängigkeit von der Eingabedatei hinzugefügt.  Das Projektsystem bestimmt automatisch den Namen der Ausgabedatei auf Grundlage der Zeichenfolge, die von der benutzerdefinierten Implementierung des Tools über <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>zurückgegeben wurde.  
  
 Ein benutzerdefiniertes Tool muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>\-Schnittstelle implementieren.  Optionale Unterstützung benutzerdefinierter Tools die <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>\-Schnittstelle, um Informationen aus den Quellen andere als die Eingabedatei abzurufen.  In jedem Fall bevor Sie ein benutzerdefiniertes Tool verwenden können, müssen Sie es im System oder in der Registrierung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Lokale registrieren.  Weitere Informationen zum Registrieren von benutzerdefinierten Tools finden Sie unter [Registrieren von Einzeldatei\-Generatoren](../../extensibility/internals/registering-single-file-generators.md).  
  
## Siehe auch  
 [Ermitteln des Standardnamespaces eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [\-Typen für visuelle Designer verfügbar gemacht](../../extensibility/internals/exposing-types-to-visual-designers.md)