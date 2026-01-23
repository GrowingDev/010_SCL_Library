# SelectOperationMode
Dieser Funktionsbaustein verwaltet und steuert die aktuelle Betriebsart der Anlage.

Voraussetzungen für die Aktivierung einer Betriebsart sind:

es liegt keine Störung an,

der Not-Aus ist nicht aktiv,

ein ggf. erforderlicher Betriebsartenwechsel wurde quittiert.

Die ausgewählte Betriebsart wird anschließend durch Betätigung des Starttasters aktiviert.

Ein anstehender Fehler, das Betätigen des Not-Aus oder ein quittierter Wechsel der Betriebsart führen zur Deaktivierung der aktuell aktiven Betriebsart.

Die dazugehörigen Signalleuchten werden ebenfalls gesteuert