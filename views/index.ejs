const express = require('express');
const path = require('path');
const opcua = require('node-opcua');

const app = express();
const port = 3000;

// Set up the OPC UA client
const endpointUrl = 'opc.tcp://127.0.0.1:4840';
const client = new opcua.OPCUAClient();

app.use(express.urlencoded({ extended: true }));
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

// Define routes
app.get('/', (req, res) => {
    res.render('index');
});

app.post('/readPressure', async (req, res) => {
    try {
        await client.connect(endpointUrl);

        const session = await client.createSession();
        const nodeId = 'ns=2;i=4';
        const dataValue = await session.readVariableValue(nodeId);

        await session.close();
        await client.disconnect();

        res.json({ pressure: dataValue.value.value });
    } catch (error) {
        console.error('Error reading pressure:', error.message);
        res.status(500).json({ error: 'Internal Server Error' });
    }
});

app.post('/writePressure', async (req, res) => {
    try {
        await client.connect(endpointUrl);

        const session = await client.createSession();
        const nodeId = 'ns=2;i=4';
        const newPressureValue = parseFloat(req.body.newPressureValue);
        await session.writeSingleNode(nodeId, new opcua.Variant({ dataType: opcua.DataType.Double, value: newPressureValue }));

        await session.close();
        await client.disconnect();

        res.json({ success: true });
    } catch (error) {
        console.error('Error writing pressure:', error.message);
        res.status(500).json({ error: 'Internal Server Error' });
    }
});

// Start the server
app.listen(port, () => {
    console.log(`Server is running at http://localhost:${port}`);
});
