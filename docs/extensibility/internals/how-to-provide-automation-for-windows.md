---
title: 'Vorgehensweise: Bereitstellen von Automatisierung für Windows | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a4482069d16ef6f0f64472b838057949890a6d3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335154"
---
# <a name="how-to-provide-automation-for-windows"></a>Vorgehensweise: Bereitstellen von Automatisierung für windows

Sie können Automation für die Dokument- und-Toolfenster bereitstellen. Bietet Automation empfiehlt sich, wenn Sie Automatisierungsobjekte in einem Fenster verfügbar machen möchten, und die Umgebung noch nicht bieten Sie eine vorgefertigte Automatisierungsobjekt, wie mit einer Aufgabenliste.

## <a name="automation-for-tool-windows"></a>Automatisierung für Toolfenster

Die Umgebung ermöglicht eine Automatisierung durch Zurückgeben von Standard in einem Toolfenster <xref:EnvDTE.Window> Objekt wie im folgenden Verfahren beschrieben:

1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode über die Umgebung mit [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) als `VSFPROPID` Parameter, um die `Window` Objekt.

2.  Wenn ein Aufrufer eine VSPackage-spezifisches Automatisierungsobjekt für das Toolfenster über anfordert <xref:EnvDTE.Window.Object%2A>, die Umgebung ruft `QueryInterface` für `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, oder die `IDispatch` Schnittstellen. Beide `IExtensibleObject` und `IVsExtensibleObject` bieten eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> Methode.

3.  Wenn die Umgebung anschließend ruft der `GetAutomationObject` -Methode und übergeben Sie `NULL`, reagieren, indem Sie übergeben sichern Ihre VSPackage-Objekt.

4.  Wenn der Aufruf `QueryInterface` für `IExtensibleObject` und `IVsExtensibleObject` ein Fehler auftritt, und klicken Sie dann die Umgebung ruft `QueryInterface` für `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatisierung für Dokumentfenster

Ein Standard <xref:EnvDTE.Document> Objekt steht auch über die Umgebung, auch ein Editor eine eigene Implementierung von verfügen, kann die <xref:EnvDTE.Document> Objekt durch die Implementierung `IExtensibleObject` -Schnittstelle von und reagieren auf `GetAutomationObject`.

Darüber hinaus bieten ein Editor ein VSPackage-spezifisches Automatisierungsobjekt, abrufen, der über die <xref:EnvDTE.Document.Object%2A> Methode, durch die Implementierung der `IVsExtensibleObject` oder `IExtensibleObject` Schnittstellen. Die [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples) ein RTF-Automatisierungsobjekt dokumentspezifische beiträgt.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>