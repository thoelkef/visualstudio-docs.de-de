---
title: 'Gewusst wie: Bereitstellen von Automatisierung für Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707949"
---
# <a name="how-to-provide-automation-for-windows"></a>Gewusst wie: Bereitstellen von Automatisierung für Fenster

Sie können die Automatisierung für Dokument- und Werkzeugfenster bereitstellen. Die Bereitstellung von Automatisierung ist ratsam, wenn Sie Automatisierungsobjekte in einem Fenster verfügbar machen möchten, und die Umgebung stellt noch kein vorgefertigtes Automatisierungsobjekt bereit, wie dies bei einer Aufgabenliste der Fall ist.

## <a name="automation-for-tool-windows"></a>Automatisierung für Werkzeugfenster

Die Umgebung stellt die Automatisierung eines <xref:EnvDTE.Window> Werkzeugfensters bereit, indem ein Standardobjekt zurückgegeben wird, wie im folgenden Verfahren erläutert:

1. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Sie die Methode über die Umgebung mit [__VSFPROPID auf. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` als Parameter, `Window` um das Objekt abzubekommen.

2. Wenn ein Aufrufer ein VSPackage-spezifisches Automatisierungsobjekt für Ihr `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>Toolfenster `IDispatch` durch <xref:EnvDTE.Window.Object%2A>anfordert, ruft `QueryInterface` die Umgebung nach , oder die Schnittstellen auf. `IExtensibleObject` Beides `IVsExtensibleObject` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> bieten eine Methode.

3. Wenn die Umgebung `GetAutomationObject` dann `NULL`die Methode passing aufruft, antworten Sie, indem Sie Ihr VSPackage-spezifisches Objekt zurückgeben.

4. Wenn `QueryInterface` `IExtensibleObject` dies `IVsExtensibleObject` der Aufruf und `QueryInterface` `IDispatch`das Scheitern der Aufforderung ist, fordert die Umgebung .

## <a name="automation-for-document-windows"></a>Automatisierung für Dokumentfenster

Ein <xref:EnvDTE.Document> Standardobjekt ist auch in der Umgebung verfügbar, obwohl <xref:EnvDTE.Document> ein Editor `IExtensibleObject` über eine `GetAutomationObject`eigene Implementierung des Objekts verfügen kann, indem er die Schnittstelle implementiert und auf reagiert.

Darüber hinaus kann ein Editor ein VSPackage-spezifisches <xref:EnvDTE.Document.Object%2A> Automatisierungsobjekt bereitstellen, das über die Methode abgerufen wird, indem er die `IVsExtensibleObject` oder `IExtensibleObject` Schnittstellen implementiert. Die [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples) tragen ein DOKUMENTspezifisches RTF-Automatisierungsobjekt bei.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
