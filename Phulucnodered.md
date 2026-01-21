[
    {
        "id": "tab_main",
        "type": "tab",
        "label": "INA219 RS485 Monitor",
        "disabled": false
    },
    {
        "id": "inject_poll",
        "type": "inject",
        "z": "tab_main",
        "name": "Poll 1s",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "60",
        "crontab": "",
        "once": false,
        "onceDelay": "1",
        "topic": "",
        "payload": "",
        "payloadType": "num",
        "x": 260,
        "y": 580,
        "wires": [
            [
                "aa51e907faf1ecf0"
            ]
        ]
    },
    {
        "id": "read_v",
        "type": "modbus-read",
        "z": "tab_main",
        "name": "Voltage – Slave 1",
        "topic": "",
        "showStatusActivities": false,
        "logIOActivities": false,
        "showErrors": false,
        "showWarnings": true,
        "unitid": "1",
        "dataType": "HoldingRegister",
        "adr": "0",
        "quantity": "1",
        "rate": "1",
        "rateUnit": "s",
        "delayOnStart": false,
        "enableDeformedMessages": false,
        "startDelayTime": "",
        "server": "mb_client",
        "useIOFile": false,
        "ioFile": "",
        "useIOForPayload": false,
        "emptyMsgOnFail": false,
        "x": 320,
        "y": 40,
        "wires": [
            [
                "fn_v"
            ],
            []
        ]
    },
    {
        "id": "fn_v",
        "type": "function",
        "z": "tab_main",
        "name": "Voltage /100",
        "func": "msg.payload = msg.payload.voltage;\nreturn msg;",
        "outputs": 1,
        "timeout": "",
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 560,
        "y": 40,
        "wires": [
            [
                "chart_v",
                "ui_style"
            ]
        ]
    },
    {
        "id": "read_i",
        "type": "modbus-read",
        "z": "tab_main",
        "name": "Current – Slave 2",
        "topic": "",
        "showStatusActivities": false,
        "logIOActivities": false,
        "showErrors": false,
        "showWarnings": true,
        "unitid": "2",
        "dataType": "HoldingRegister",
        "adr": "0",
        "quantity": "1",
        "rate": "1",
        "rateUnit": "s",
        "delayOnStart": false,
        "enableDeformedMessages": false,
        "startDelayTime": "",
        "server": "mb_client",
        "useIOFile": false,
        "ioFile": "",
        "useIOForPayload": false,
        "emptyMsgOnFail": false,
        "x": 320,
        "y": 120,
        "wires": [
            [
                "fn_i"
            ],
            []
        ]
    },
    {
        "id": "fn_i",
        "type": "function",
        "z": "tab_main",
        "name": "Current /100",
        "func": "msg.payload = msg.payload.current;\nreturn msg;\n",
        "outputs": 1,
        "timeout": "",
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 560,
        "y": 100,
        "wires": [
            [
                "ui_i",
                "chart_i"
            ]
        ]
    },
    {
        "id": "read_p",
        "type": "modbus-read",
        "z": "tab_main",
        "name": "Power – Slave 3",
        "unitid": "3",
        "dataType": "HoldingRegister",
        "adr": "0",
        "quantity": "1",
        "rate": "1",
        "rateUnit": "s",
        "server": "mb_client",
        "x": 320,
        "y": 200,
        "wires": [
            [
                "fn_p"
            ],
            []
        ]
    },
    {
        "id": "fn_p",
        "type": "function",
        "z": "tab_main",
        "name": "Power /100",
        "func": "msg.payload = msg.payload.power;\nreturn msg;",
        "outputs": 1,
        "timeout": "",
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 560,
        "y": 160,
        "wires": [
            [
                "ui_p",
                "chart_p"
            ]
        ]
    },
    {
        "id": "ui_v",
        "type": "ui-gauge",
        "z": "tab_main",
        "name": "Bus Voltage",
        "group": "grp_top",
        "order": 1,
        "value": "payload",
        "valueType": "msg",
        "width": 4,
        "height": 4,
        "gtype": "gauge-half",
        "gstyle": "needle",
        "title": "Bus Voltage (V)",
        "alwaysShowTitle": false,
        "units": "",
        "icon": "flash",
        "prefix": "",
        "suffix": "",
        "segments": [],
        "min": 5,
        "max": 8,
        "sizeThickness": "15",
        "sizeGap": "5",
        "sizeKeyThickness": "6",
        "className": "gauge-voltage",
        "x": 1010,
        "y": 80,
        "wires": [
            []
        ]
    },
    {
        "id": "ui_i",
        "type": "ui-gauge",
        "z": "tab_main",
        "name": "Current",
        "group": "grp_top",
        "order": 2,
        "value": "payload",
        "valueType": "msg",
        "width": 4,
        "height": 4,
        "gtype": "gauge-half",
        "gstyle": "needle",
        "title": "Current (A)",
        "alwaysShowTitle": false,
        "units": "",
        "icon": "",
        "prefix": "",
        "suffix": "",
        "segments": [],
        "min": 0,
        "max": 2,
        "sizeThickness": "15",
        "sizeGap": "5",
        "sizeKeyThickness": "6",
        "className": "gauge-current",
        "x": 1000,
        "y": 200,
        "wires": [
            []
        ]
    },
    {
        "id": "ui_p",
        "type": "ui-gauge",
        "z": "tab_main",
        "name": "Power",
        "group": "grp_top",
        "order": 3,
        "value": "payload",
        "valueType": "msg",
        "width": 4,
        "height": 4,
        "gtype": "gauge-half",
        "gstyle": "needle",
        "title": "Power (W)",
        "alwaysShowTitle": false,
        "units": "",
        "icon": "",
        "prefix": "",
        "suffix": "",
        "segments": [],
        "min": 0,
        "max": 15,
        "sizeThickness": "15",
        "sizeGap": "5",
        "sizeKeyThickness": "6",
        "className": "gauge-power",
        "x": 990,
        "y": 260,
        "wires": [
            []
        ]
    },
    {
        "id": "chart_v",
        "type": "ui-chart",
        "z": "tab_main",
        "group": "grp_bottom",
        "name": "Voltage Chart",
        "label": "Voltage vs Time",
        "order": 1,
        "chartType": "line",
        "category": "topic",
        "categoryType": "msg",
        "xAxisLabel": "Time",
        "xAxisProperty": "",
        "xAxisPropertyType": "timestamp",
        "xAxisType": "time",
        "xAxisFormat": "",
        "xAxisFormatType": "auto",
        "xmin": "",
        "xmax": "",
        "yAxisLabel": "Voltage (V)",
        "yAxisProperty": "payload",
        "yAxisPropertyType": "msg",
        "ymin": "0",
        "ymax": "8",
        "bins": "",
        "stackSeries": false,
        "pointRadius": "",
        "showLegend": true,
        "removeOlder": "1",
        "removeOlderUnit": "60",
        "removeOlderPoints": "",
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "textColor": [
            "#666666"
        ],
        "textColorDefault": true,
        "gridColor": [
            "#e5e5e5"
        ],
        "gridColorDefault": true,
        "width": 12,
        "height": 4,
        "className": "",
        "interpolation": "linear",
        "x": 1020,
        "y": 40,
        "wires": [
            []
        ]
    },
    {
        "id": "chart_i",
        "type": "ui-chart",
        "z": "tab_main",
        "group": "grp_bottom",
        "name": "Current Chart",
        "label": "Current vs Time",
        "order": 2,
        "chartType": "line",
        "category": "topic",
        "categoryType": "msg",
        "xAxisLabel": "Time",
        "xAxisProperty": "",
        "xAxisPropertyType": "timestamp",
        "xAxisType": "time",
        "xAxisFormat": "",
        "xAxisFormatType": "auto",
        "xmin": "",
        "xmax": "",
        "yAxisLabel": "Curent (A)",
        "yAxisProperty": "payload",
        "yAxisPropertyType": "msg",
        "ymin": "0",
        "ymax": "8",
        "bins": "",
        "stackSeries": false,
        "pointRadius": "",
        "showLegend": true,
        "removeOlder": "1",
        "removeOlderUnit": "60",
        "removeOlderPoints": "",
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "textColor": [
            "#666666"
        ],
        "textColorDefault": true,
        "gridColor": [
            "#e5e5e5"
        ],
        "gridColorDefault": true,
        "width": 12,
        "height": 4,
        "className": "",
        "interpolation": "linear",
        "x": 1020,
        "y": 140,
        "wires": [
            []
        ]
    },
    {
        "id": "chart_p",
        "type": "ui-chart",
        "z": "tab_main",
        "group": "grp_bottom",
        "name": "Power Chart",
        "label": "Power vs Time",
        "order": 3,
        "chartType": "line",
        "category": "topic",
        "categoryType": "msg",
        "xAxisLabel": "Time",
        "xAxisProperty": "",
        "xAxisPropertyType": "timestamp",
        "xAxisType": "time",
        "xAxisFormat": "",
        "xAxisFormatType": "auto",
        "xmin": "",
        "xmax": "",
        "yAxisLabel": "Power (P)",
        "yAxisProperty": "payload",
        "yAxisPropertyType": "msg",
        "ymin": "0",
        "ymax": "15",
        "bins": "",
        "stackSeries": false,
        "pointRadius": "",
        "showLegend": true,
        "removeOlder": "1",
        "removeOlderUnit": "60",
        "removeOlderPoints": "",
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "textColor": [
            "#666666"
        ],
        "textColorDefault": true,
        "gridColor": [
            "#e5e5e5"
        ],
        "gridColorDefault": true,
        "width": 12,
        "height": 4,
        "className": "",
        "interpolation": "linear",
        "x": 1010,
        "y": 320,
        "wires": [
            []
        ]
    },
    {
        "id": "ui_style",
        "type": "ui-template",
        "z": "tab_main",
        "group": "",
        "page": "1748916a0dd36ce3",
        "ui": "",
        "name": "",
        "order": 2,
        "width": 12,
        "height": 1,
        "format": "/* ================== GLOBAL BACKGROUND ================== */\nbody {\n  background-color: #f4f6f8 !important;\n  font-family: \"Segoe UI\", Roboto, Arial, sans-serif;\n}\n\n/* ================== COMMON GAUGE STYLE ================== */\n.gauge-voltage,\n.gauge-current,\n.gauge-power {\n  background-color: #ffffff;\n  border-radius: 14px;\n  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);\n  padding: 6px;\n}\n\n/* Track chung */\n.gauge-voltage svg path.track,\n.gauge-current svg path.track,\n.gauge-power svg path.track {\n  stroke: #e0e0e0 !important;\n}\n\n/* Text chung */\n.gauge-voltage text,\n.gauge-current text,\n.gauge-power text {\n  fill: #333333 !important;\n  font-weight: 600;\n}\n\n/* ================== VOLTAGE GAUGE ================== */\n.gauge-voltage svg path.value {\n  stroke: #2ecc71 !important;   /* Xanh lá */\n}\n\n/* ================== CURRENT GAUGE ================== */\n.gauge-current svg path.value {\n  stroke: #3498db !important;   /* Xanh dương */\n}\n\n/* ================== POWER GAUGE ================== */\n.gauge-power svg path.value {\n  stroke: #f39c12 !important;   /* Cam */\n}\n",
        "storeOutMessages": true,
        "passthru": true,
        "templateScope": "page:style",
        "className": "",
        "x": 810,
        "y": 80,
        "wires": [
            [
                "ui_v"
            ]
        ]
    },
    {
        "id": "aa51e907faf1ecf0",
        "type": "function",
        "z": "tab_main",
        "name": "function 1",
        "func": "// Giả lập điện áp bus (pin + buck): 6.2 – 7.4 V\nlet voltage = 6.2 + Math.random() * 1.2;\n\n// Giả lập dòng đèn: 0.4 – 1.6 A\nlet current = 0.4 + Math.random() * 1.2;\n\n// Công suất thật P = U * I\nlet power = voltage * current;\n\n// Làm tròn cho đẹp\nmsg.payload = {\n    voltage: Number(voltage.toFixed(2)),\n    current: Number(current.toFixed(2)),\n    power: Number(power.toFixed(2))\n};\n\nreturn msg;\n",
        "outputs": 1,
        "timeout": 0,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 500,
        "y": 540,
        "wires": [
            []
        ]
    },
    {
        "id": "mb_client",
        "type": "modbus-client",
        "name": "RS485 Modbus RTU",
        "clienttype": "serial"
    },
    {
        "id": "grp_top",
        "type": "ui-group",
        "name": "Realtime Parameters",
        "page": "1748916a0dd36ce3",
        "width": "12",
        "height": "",
        "order": 1,
        "showTitle": true,
        "className": "",
        "visible": "true",
        "disabled": "false",
        "groupType": "default"
    },
    {
        "id": "grp_bottom",
        "type": "ui-group",
        "name": "Realtime Charts",
        "page": "1748916a0dd36ce3",
        "width": "12",
        "height": "",
        "order": 2,
        "showTitle": true,
        "className": "",
        "visible": "true",
        "disabled": "false",
        "groupType": "default"
    },
    {
        "id": "1748916a0dd36ce3",
        "type": "ui-page",
        "name": "HỆ THỐNG GIÁM SÁT",
        "ui": "df89429abab75b25",
        "path": "/page1",
        "icon": "home",
        "layout": "grid",
        "theme": "79aa97c885b7061a",
        "breakpoints": [
            {
                "name": "Default",
                "px": "0",
                "cols": "3"
            },
            {
                "name": "Tablet",
                "px": "576",
                "cols": "6"
            },
            {
                "name": "Small Desktop",
                "px": "768",
                "cols": "9"
            },
            {
                "name": "Desktop",
                "px": "1024",
                "cols": "12"
            }
        ],
        "order": 1,
        "className": "",
        "visible": "true",
        "disabled": "false"
    },
    {
        "id": "df89429abab75b25",
        "type": "ui-base",
        "name": "UI Name",
        "path": "/dashboard",
        "appIcon": "",
        "includeClientData": true,
        "acceptsClientConfig": [
            "ui-notification",
            "ui-control"
        ],
        "showPathInSidebar": false,
        "headerContent": "page",
        "navigationStyle": "default",
        "titleBarStyle": "default",
        "showReconnectNotification": true,
        "notificationDisplayTime": 1,
        "showDisconnectNotification": true,
        "allowInstall": true
    },
    {
        "id": "79aa97c885b7061a",
        "type": "ui-theme",
        "name": "Theme Name",
        "colors": {
            "surface": "#ffffff",
            "primary": "#0094ce",
            "bgPage": "#ededed",
            "groupBg": "#ffffff",
            "groupOutline": "#cccccc"
        },
        "sizes": {
            "density": "default",
            "pagePadding": "12px",
            "groupGap": "12px",
            "groupBorderRadius": "4px",
            "widgetGap": "12px"
        }
    },
    {
        "id": "551ead3af1dd20d4",
        "type": "global-config",
        "env": [],
        "modules": {
            "node-red-contrib-modbus": "5.45.2",
            "@flowfuse/node-red-dashboard": "1.30.1"
        }
    }
]
