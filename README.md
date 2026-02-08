**Real-Time CDC with MongoDB & Python**

This project demonstrates real-time Change Data Capture (CDC) using MongoDB Change Streams and a lightweight Python pipeline. All change events (insert, update, delete) are captured and written to the local file system.

**Prerequisites**

* MongoDB (Replica Set enabled)
* Python 3.10+
* PyMongo

**Step 1: Start MongoDB with Replica Set**

mongod --dbpath ~/mongodb/data --replSet rs0
Initialize replica set (only first time):

rs.initiate()

**Step 2: Install Python Dependencies**

pip install pymongo

**Step 3: Run the CDC Python Script**

Real_Time_CDC_Python_Version_1.py

You should see:

Listening for real-time CDC events...

**Step 4: Open Mongo Shell**

mongosh

Switch to database:

use realtime_cdc

**Step 5: Test CDC (Insert / Update / Delete)**


**Insert – Order Placed**

db.orders.insertOne({
  order_id: 101,
  customer: "Aravind",
  amount: 25000,
  status: "Placed"
})

**Update – Order Cancelled**

db.orders.updateOne(
  { order_id: 101 },
  { $set: { status: "Cancelled" } }
)

**Delete – Order Removed**

db.orders.deleteOne({ order_id: 101 })

📂 Output
* CDC events are written to the local file system
* Folder structure follows a data lake pattern (year/month/day)
Example:

data_lake/orders/year=2026/month=01/day=24/

use realtime_cdc

