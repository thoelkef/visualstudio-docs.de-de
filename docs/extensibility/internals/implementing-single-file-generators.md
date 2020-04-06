---
title: Implementieren von Single-File-Generatoren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707653"
---
# <a name="implementing-single-file-generators"></a>Implementieren von Generatoren einzelner Dateien
Ein benutzerdefiniertes Tool , das manchmal als einzelner Dateigenerator [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] bezeichnet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wird , kann verwendet werden, um die und die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projektsysteme in zu erweitern. Ein benutzerdefiniertes Tool ist eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM-Komponente, die die Schnittstelle implementiert. Mithilfe dieser Schnittstelle wandelt ein benutzerdefiniertes Tool eine einzelne Eingabedatei in eine einzelne Ausgabedatei um. Das Ergebnis der Transformation kann Quellcode oder eine andere Ausgabe sein, die nützlich ist. Zwei Beispiele für benutzerdefinierte toolgenerierte Codedateien sind Code, der als Reaktion auf Änderungen in einem visuellen Designer generiert wird, und Dateien, die mit Web Services Description Language (WSDL) generiert werden.

 Wenn ein benutzerdefiniertes Werkzeug geladen oder die Eingabedatei <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> gespeichert wird, ruft das <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> Projektsystem die Methode auf und übergibt einen Verweis auf eine Rückrufschnittstelle, wodurch das Werkzeug seinen Fortschritt an den Benutzer melden kann.

 Die Ausgabedatei, die das benutzerdefinierte Tool generiert, wird dem Projekt mit einer Abhängigkeit von der Eingabedatei hinzugefügt. Das Projektsystem ermittelt automatisch den Namen der Ausgabedatei, basierend auf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Zeichenfolge, die von der Implementierung des benutzerdefinierten Tools von zurückgegeben wird.

 Ein benutzerdefiniertes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Tool muss die Schnittstelle implementieren. Optional unterstützen benutzerdefinierte <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> Tools die Schnittstelle zum Abrufen von Informationen aus anderen Quellen als der Eingabedatei. In jedem Fall müssen Sie es, bevor Sie ein benutzerdefiniertes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tool verwenden können, beim System oder in der lokalen Registrierung registrieren. Weitere Informationen zum Registrieren benutzerdefinierter Tools finden Sie unter [Registrieren von Einzelnen Dateigeneratoren](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Weitere Informationen
- [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)
