---
title: 'Vorgehensweise: Bereitstellen von Automatisierung für Windows | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848857"
---
# <a name="how-to-provide-automation-for-windows"></a>Vorgehensweise: Bereitstellen von Automatisierung für Windows

Sie können die Automatisierung für Dokument-und Tool Fenster bereitstellen. Das Bereitstellen von Automatisierung ist ratsam, wenn Sie Automation-Objekte in einem Fenster verfügbar machen möchten und die Umgebung nicht bereits ein vorgefertigte Automatisierungs Objekt bereitstellt, wie es bei einer Aufgabenliste der Fall ist.

## <a name="automation-for-tool-windows"></a>Automatisierung für Tool Fenster

Die Umgebung ermöglicht die Automatisierung in einem Tool Fenster, indem ein Standard <xref:EnvDTE.Window> Objekt zurückgegeben wird, wie im folgenden Verfahren erläutert:

1. Nennen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>-Methode über die Umgebung mit [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) als `VSFPROPID` Parameter, um das `Window`-Objekt zu erhalten.

2. Wenn ein Aufrufer über <xref:EnvDTE.Window.Object%2A>ein VSPackage-spezifisches Automatisierungs Objekt für das Tool Fenster anfordert, ruft die Umgebung `QueryInterface` für `IExtensibleObject`-, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>-oder `IDispatch`-Schnittstellen auf. Sowohl `IExtensibleObject` als auch `IVsExtensibleObject` stellen eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>-Methode bereit.

3. Wenn die Umgebung dann die `GetAutomationObject` Methode aufruft, die `NULL`übergibt, reagieren Sie, indem Sie das VSPackage-spezifische Objekt zurück übergeben.

4. Wenn der Aufruf von `QueryInterface` für `IExtensibleObject` und `IVsExtensibleObject` fehlschlägt, ruft die Umgebung `QueryInterface` für `IDispatch`auf.

## <a name="automation-for-document-windows"></a>Automatisierung für Dokument Fenster

Ein Standard <xref:EnvDTE.Document>-Objekt ist auch in der-Umgebung verfügbar, obwohl ein Editor über eine eigene Implementierung des <xref:EnvDTE.Document> Objekts verfügen kann, indem `IExtensibleObject`-Schnittstelle implementiert wird und auf `GetAutomationObject`reagiert wird.

Außerdem kann ein Editor ein VSPackage-spezifisches Automatisierungs Objekt bereitstellen, das durch die <xref:EnvDTE.Document.Object%2A>-Methode abgerufen wird, indem die `IVsExtensibleObject`-oder `IExtensibleObject`-Schnittstellen implementiert werden. Die [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples) tragen zu einem RTF-Dokument spezifischen Automatisierungs Objekt bei.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
