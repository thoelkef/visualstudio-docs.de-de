---
title: Programmieren mit Visual Studio-Tools für Unity | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d70a2fe335b89d18e31128fa284d44d74130c127
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programmieren mit Visual Studio-Tools für Unity
In diesem Abschnitt finden Sie Beispiele für die Verwendung der Visual Studio-Tools für Unity-API.

## <a name="examples"></a>Beispiele
 Hier sind einige Beispiele, die zeigen, wie Sie Visual Studio-Tools für Unity-APIs verwenden können.

### <a name="customize-project-files-created-by-vstu"></a>Anpassen von mit VSTU erstellten Projektdateien
 Visual Studio-Tools für Unity bieten während der Generierung der Projektdatei einen Rückruf im Unity-Stil. Informationen dazu, wie Sie die Projektdatei ändern können, immer wenn sie erneut generiert wird, finden Sie unter [Beispiel: Erstellung der Projektdatei](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Freigeben des Unity-Protokollrückrufs für VSTU
 Visual Studio-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann. Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU-Rückruf Ihren Rückruf stören. Informationen dazu, wie Sie den Unity-Protokollrückruf für VSTU freigeben können, finden Sie unter [Beispiel: Protokollrückruf](../cross-platform/share-the-unity-log-callback-with-vstu.md).
