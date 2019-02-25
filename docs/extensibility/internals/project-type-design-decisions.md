---
title: Entwurfsentscheidungen bei Projekttypen Projekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e420261810cec793cc553eac83bbc97edd1fb1c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634539"
---
# <a name="project-type-design-decisions"></a>Entwurfsentscheidungen bei Projekttypen
Bevor Sie einen neuen Projekttyp erstellen, müssen Sie einige entwurfsentscheidungen in Bezug auf die Art Ihres Projekts. Sie müssen entscheiden, welche Elemente, die Ihre Projekte enthält, wie Project-Dateien beibehalten werden und welche Verpflichtung Modell Sie verwenden möchten.

## <a name="project-items"></a>Projektelemente
 Wird Ihr Projekt verwenden, Dateien oder abstrakte Objekte? Wenn Sie Dateien verwenden, werden sie anhand von verweisen oder Directory-basierte Dateien? Werden die Dateien und die abstrakte Objekte, die im lokalen oder Remotecomputer sein?

 Die Elemente in einem Projekt können Dateien sein, oder sie können die eher abstrakte Objekte, z. B. Objekte in einer Datenbank-Repository oder die datenverbindungen sein, über das Internet. Wenn die Elemente Dateien befinden, kann das Projekt entweder eine verweisbasierte oder ein Verzeichnisbasiertes Projekt sein.

 Im Verweis-basierten Projekten können die Elemente in mehr als ein Projekt angezeigt werden. Jedoch befindet sich die Datei, die ein Element darstellt, in nur einem Verzeichnis. Im Verzeichnis-basierte Projekte sind Sie alle Projektelemente in die Verzeichnisstruktur vorhanden.

 Lokale Elemente werden auf demselben Computer gespeichert, in dem die Anwendung installiert wird. Remote-Elemente können auf einem separaten Server in einem lokalen Netzwerk oder an anderer Stelle im Internet gespeichert werden.

## <a name="project-file-persistence"></a>Project-Datei-Persistenz
 Werden Daten in gängige Systeme für Flatfile-Datei oder in strukturierten Speicher werden gespeichert? Werden Dateien mit einem standard-Editor oder einen projektspezifischen Editor werden geöffnet?

 Um ihre Daten beizubehalten, die meisten Anwendungen speichern ihre Daten in eine Datei, und klicken Sie dann zurück, wenn ein Benutzer muss überprüfen oder ändern Sie die Informationen lesen.

 Strukturierter Speicher, compound-Dateien, so genannte wird normalerweise verwendet, wenn mehrere Objekte von Component Object Model (COM) ihrer persistenten Daten in einer einzigen Datei speichern müssen. Mit dem strukturierten Speicher können mehrere verschiedenen Softwarekomponenten Datei auf einem einzelnen Datenträger freigeben.

 Sie haben mehrere Optionen, um in Bezug auf Dauerhaftigkeit für die Elemente in Ihrem Projekt berücksichtigen. Sie können eine der folgenden Optionen ausführen:

- Speichern Sie jede Datei einzeln aus, wenn es geändert wurde.

- Erfassen Sie viele Transaktionen in einem einzelnen **speichern** Vorgang.

- Speichern Sie Dateien lokal, und klicken Sie dann auf einem Server veröffentlichen Sie, oder verwenden Sie ein weiteres Verfahren zum Speichern von Projektelementen, wenn das Element eine Verbindung mit einem Remoteobjekt darstellt.

  Weitere Informationen zu Persistenz finden Sie unter [Projektpersistenz](../../extensibility/internals/project-persistence.md) und [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Engagement-Projektmodell
 Persistente Datenobjekte geöffnet werden im direkten Modus oder im transaktiven Modus?

 Wenn Datenobjekte im direkten Modus geöffnet sind, werden an den Daten vorgenommenen Änderungen integriert, sofort aus, oder wenn der Benutzer manuell die Datei speichert.

 Wenn Data-Objekte mithilfe von transaktiven Modus geöffnet sind, werden Änderungen an einem temporären Speicherort im Arbeitsspeicher gespeichert werden und werden kein Commit ausgeführt, bis der Benutzer manuell zum Speichern der Datei. Zu diesem Zeitpunkt alle Änderungen müssen zusammen auftreten, oder werden keine Änderungen vorgenommen.

## <a name="see-also"></a>Siehe auch
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Projektpersistenz](../../extensibility/internals/project-persistence.md)
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)
- [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)
- [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)