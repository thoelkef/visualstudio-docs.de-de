---
title: 'Vorgehensweise: Erstellen in einem allgemeinen Ausgabeverzeichnis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f45890224684ff2e4c411875ab61bdfb698cfb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942044"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Vorgehensweise: Erstellen in einem allgemeinen Ausgabeverzeichnis

Standardmäßig erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jedes Projekt in einer Projektmappe in einem eigenen Ordner in der Projektmappe. Sie können die Buildausgabepfade Ihrer Projekte so ändern, dass alle Ausgaben im selben Ordner abgelegt werden.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>So legen Sie alle Ausgaben in einem gemeinsamen Verzeichnis ab

1.  Klicken Sie auf ein Projekt in der Projektmappe.

2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

3.  Klicken Sie je nach Art des Projekts auf die Registerkarte **Kompilieren** oder **Erstellen**, und legen Sie den **Ausgabepfad** für alle Projekte in der Projektmappe auf denselben Ordner fest.

4.  Wiederholen Sie die Schritte 1 bis 3 für alle Projekte in der Projektmappe.

## <a name="see-also"></a>Siehe auch

- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
- [Vorgehensweise: Ändern des Buildausgabeverzeichnisses](../ide/how-to-change-the-build-output-directory.md)