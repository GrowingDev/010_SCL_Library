# FB Modes of operation

Author: Andreas Benz
Created at: 06.01.2026

## INPUTS

IN_Btn_start: BOOL  [Kommentar]: 
IN_Btn_stop: BOOL
IN_Btn_ACK: BOOL
IN_Fault: BOOL
IN_Sw_Auto: BOOL
IN_Sw_Emergency_off: BOOL

## OUTPUTS

OUT_mode_auto: BOOL
OUT_mode_manual: BOOL
OUT_LED_auto: BOOL
OUT_LED_manual: BOOL
OUT_LED_ACK: BOOL
OUT_LED_Stop: BOOL

Dieser Funktionsbaustein verwaltet und steuert die aktuelle Betriebsart der Anlage.

Voraussetzungen für die Aktivierung einer Betriebsart sind:

es liegt keine Störung an,

der Not-Aus ist nicht aktiv,

ein ggf. erforderlicher Betriebsartenwechsel wurde quittiert.

Die ausgewählte Betriebsart wird anschließend durch Betätigung des Starttasters aktiviert.

Ein anstehender Fehler, das Betätigen des Not-Aus oder ein quittierter Wechsel der Betriebsart führen zur Deaktivierung der aktuell aktiven Betriebsart.