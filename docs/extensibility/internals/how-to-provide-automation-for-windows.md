---
title: "Vorgehensweise: Bereitstellen von Automation für Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17cf60573b6feb9fd317116eec4639dbf88f6089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-automation-for-windows"></a>Vorgehensweise: Bereitstellen von Automation für Windows
Sie können die Automatisierung Dokument-und Toolfenstern bereitzustellen. Mit der Automatisierung ist ratsam, wenn Sie in einem Fenster Automatisierungsobjekte verfügbar machen möchten, und die Umgebung noch nicht bieten Sie eine vorgefertigte Automatisierungsobjekt wie bei eine Aufgabenliste.  
  
## <a name="automation-for-tool-windows"></a>Automatisierung für Toolfenster  
 Die Umgebung ermöglicht eine Automatisierung auf einem Toolfenster wird durch Zurückgeben von einer standardmäßiges <xref:EnvDTE.Window> Objekt wie im folgenden Verfahren beschrieben:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Um Automatisierung für Toolfenster bereitzustellen  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode über die Umgebung mit <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> als `VSFPROPID` Parameter zum Abrufen der `Window` Objekt.  
  
2.  Wenn ein Aufrufer eine VSPackage-spezifische Automatisierungsobjekt für Ihr Toolfenster über anfordert <xref:EnvDTE.Window.Object%2A>, die Umgebung ruft `QueryInterface` für `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, oder die `IDispatch` Schnittstellen. Beide `IExtensibleObject` und `IVsExtensibleObject` bieten eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> Methode.  
  
3.  Wenn die Umgebung dann ruft der `GetAutomationObject` Methode übergeben `NULL`, Antworten durch Übergabe sichern Ihre VSPackage-Objekt.  
  
4.  Wenn der Aufruf `QueryInterface` für `IExtensibleObject` und `IVsExtensibleObject` ein Fehler auftritt, und klicken Sie dann die Umgebung ruft `QueryInterface` für `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automatisierung für Dokumentfenster  
 Ein Standard <xref:EnvDTE.Document> Objekt steht auch über die Umgebung, auch ein Editor ihre eigene Implementierung verfügen, kann die `T:EnvDTE.Document` Objekt durch die Implementierung `IExtensibleObject` Schnittstelle und reagieren auf `GetAutomationObject`.  
  
 Darüber hinaus bieten ein Editor ein VSPackage-spezifische Automation-Objekt abgerufen, die über die <xref:EnvDTE.Document.Object%2A> Methode, durch die Implementierung der `IVsExtensibleObject` oder `IExtensibleObject` Schnittstellen. Die [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples) ein RTF-Automatisierungsobjekt dokumentspezifische beiträgt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>