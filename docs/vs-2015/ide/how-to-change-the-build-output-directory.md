---
title: 'Gewusst wie: Ändern des Buildausgabeverzeichnisses | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645429"
---
# <a name="how-to-change-the-build-output-directory"></a>Gewusst wie: Ändern des Buildausgabeverzeichnisses
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Speicherort der vom das Projekt generierten Ausgabe auf Basis der Konfiguration („Debug“, „Release“ oder beides) angeben.

> [!NOTE]
> Wenn Sie über ein **Setup** -Projekt verfügen, beachten Sie den Hinweis am Ende dieses Artikels.

## <a name="changing-the-build-output-directory"></a>Ändern des Buildausgabeverzeichnisses

#### <a name="to-change-the-build-output-directory"></a>So ändern Sie das Buildausgabeverzeichnis

1. Wählen Sie in der Menüleiste **Projekt**und die Option *App-Name* **Eigenschaften**aus. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften**aus.

2. Wenn Sie ein Visual Basic-Projekt haben, wählen Sie die Registerkarte **Kompilieren** aus. Wenn Sie ein Visual c#-Projekt haben, wählen Sie die Registerkarte **Build** aus. Wenn Sie ein C++-Projekt oder ein JavaScript-Projekt haben, wählen Sie die Registerkarte **Allgemein** aus.

3. Wählen Sie in der Konfigurationen-Dropdownliste am oberen Rand die Konfiguration aus, deren Speicherort der Ausgabedatei Sie ändern möchten („Debug“, „Release“ oder beides).

     Suchen Sie den Eintrag des Ausgabe-Pfads (**Buildausgabepfad** in Visual Basic **Ausgabeverzeichnis** in Visual C++ **Ausgabepfad** in JavaScript und C#). Geben Sie ein neues Buildausgabeverzeichnis relativ zum Projektverzeichnis an.

> [!NOTE]
> In einem Setup-Projekt wird durch das Feld **Ausgabedateiname** lediglich der Speicherort der Datei „Setup.exe“ und nicht der Speicherort der Projektdateien geändert. Weitere Informationen finden Sie unter **Erstellen, Konfigurationseigenschaften, Bereitstellungsprojekt-Eigenschaften (Dialogfeld)**.

## <a name="see-also"></a>Weitere Informationen
 [Seite "erstellen", Projekt-Designer (c#)](../ide/reference/build-page-project-designer-csharp.md) [Allgemeine Eigenschaften Seite (Projekt)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [Kompilieren und erstellen](../ide/compiling-and-building-in-visual-studio.md)
