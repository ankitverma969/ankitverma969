import { BarChart, Bar, Line, LineChart, XAxis, YAxis, Tooltip, CartesianGrid, ResponsiveContainer, Legend, PieChart, Pie, Cell } from "recharts";

export default function GovtDashboard() {

  const attendanceData = [
    { month: "Jan", present: 22, absent: 2, leave: 2 },
    { month: "Feb", present: 20, absent: 1, leave: 4 },
    { month: "Mar", present: 24, absent: 0, leave: 1 },
  ];

  const salarySplit = [
    { name: "Basic", value: 50000 },
    { name: "HRA", value: 15000 },
    { name: "Medical", value: 5000 },
    { name: "PF", value: 6000 }
  ];

  const colors = ["#3b82f6", "#37d67a", "#facc15", "#ef4444"];

  return (
    <div className="w-full min-h-screen bg-[#0a1a2f] text-white p-6 flex gap-6">

      {/* Sidebar */}
      <aside className="w-60 bg-[#111d30] p-6 rounded-xl">
        <h1 className="text-lg font-bold mb-6">Govt. Dashboard</h1>
        <ul className="space-y-4 text-gray-300">
          <li>Home</li><li>Employee Profile</li><li>Attendance</li><li>Salary</li>
          <li>Documents</li><li>Grievance</li><li className="text-red-400 mt-6">Logout</li>
        </ul>
      </aside>

      {/* Main Panel */}
      <div className="flex-grow space-y-6">

        {/* Profile Header */}
        <section className="bg-[#12263e] p-6 rounded-xl">
          <h2 className="text-xl font-semibold">Employee: Rahul Kumar</h2>
          <p>ID: GOV12345 • Position: Revenue Officer</p>
        </section>

        {/* Graphs Section */}
        <div className="grid grid-cols-2 gap-6">

          {/* Attendance Chart */}
          <div className="bg-[#12263e] p-5 rounded-xl">
            <h3 className="mb-3 font-medium">Attendance Record</h3>
            <ResponsiveContainer width="100%" height={250}>
              <BarChart data={attendanceData}>
                <CartesianGrid strokeDasharray="3 3" stroke="#1e2f4a"/>
                <XAxis dataKey="month" stroke="#fff"/>
                <YAxis stroke="#fff"/>
                <Tooltip/>
                <Legend/>
                
                {/* Bars + Line */}
                <Bar dataKey="present" fill="#3b82f6" radius={[6,6,0,0]}/>
                <Bar dataKey="leave" fill="#facc15" radius={[6,6,0,0]}/>
                <Line type="monotone" dataKey="absent" stroke="#ef4444" strokeWidth={3}/>
              </BarChart>
            </ResponsiveContainer>
          </div>

          {/* Salary Pie Chart */}
          <div className="bg-[#12263e] p-5 rounded-xl">
            <h3 className="mb-3 font-medium">Salary Distribution</h3>
            <ResponsiveContainer width="100%" height={250}>
              <PieChart>
                <Pie data={salarySplit} dataKey="value" cx="50%" cy="50%" outerRadius={90}>
                  {salarySplit.map((_, i) => <Cell fill={colors[i]}/>)}
                </Pie>
                <Tooltip />
              </PieChart>
            </ResponsiveContainer>
          </div>

        </div>
      </div>
    </div>
  );
}
