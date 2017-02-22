---
title: "Gewusst wie: Bereitstellen von Automatisierung f&#252;r Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automatisierung [Visual Studio SDK] Toolfenster"
  - "Toolfenster, Automatisierung"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Bereitstellen von Automatisierung f&#252;r Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können die Automatisierung für Dokumente und Toolfenster bereitstellen.  Automatisierung bereitzustellen ist empfehlenswert, wenn Sie Automatisierungsobjekte in einem Fenster bereitstellen möchten, und die Umgebung nicht bereits enthält ein gebrauchsfertiges Automatisierungsobjekt, wie sie mit einer Aufgabenliste.  
  
## Automatisierung für Toolfenster  
 Die Umgebung wird die Automatisierung in einem Toolfenster aus dem Zurückgeben eines Standard\- <xref:EnvDTE.Window>\-Objekts bereit, wie in der folgenden Prozedur wird erklärt:  
  
#### Die Automatisierung für Toolfenster bereitstellen  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>\-Methode zur Umgebung mit <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>`VSFPROPID` als Parameter an, um das `Window`\-Objekt abzurufen.  
  
2.  Wenn ein Aufrufer um ein VSPackage\-Besondere Automatisierungsobjekt für das Toolfenster von <xref:EnvDTE.Window.Object%2A>anfordert, wird die Umgebung `QueryInterface` für `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>oder die `IDispatch`\-Schnittstellen an.  Sowohl `IExtensibleObject` und `IVsExtensibleObject` eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>\-Methode.  
  
3.  Wenn die Umgebung anschließend die `GetAutomationObject`\-Methode aufruft, die `NULL`übergibt, indem Sie zurück übergeben wird, reagiert das VSPackage\-Besondere Objekt.  
  
4.  Wenn schlägt der Aufruf von `QueryInterface` für `IExtensibleObject` und `IVsExtensibleObject` aus, und ruft die Umgebung `QueryInterface` für `IDispatch`an.  
  
## Automatisierung für Dokumentfenster  
 Ein Standardwert <xref:EnvDTE.Document>\-Objekt ist auch aus der Umgebung verfügbar, obwohl ein Editor über eine eigene Implementierung des `T:EnvDTE.Document`\-Objekts enthalten kann, indem er `IExtensibleObject`\-Schnittstelle implementiert und auf `GetAutomationObject`reagiert.  
  
 Außerdem kann ein Editor ein VSPackage\-Besondere Automatisierungsobjekt bereitstellen, durch die <xref:EnvDTE.Document.Object%2A>\-Methode abgerufen, indem die `IVsExtensibleObject` oder `IExtensibleObject`\-Schnittstellen implementiert.  [VSSDK\-Beispiele](../../misc/vssdk-samples.md) enthält ein RTF\-DOCUMENT besondere Automatisierungsobjekt bei.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>