# paitow-web
import { useState } from "react";

export default function TowingApp() { const [form, setForm] = useState({ name: "", phone: "", vehicle: "", distance: "" }); const [price, setPrice] = useState(null);

const handleChange = (e) => { setForm({ ...form, [e.target.name]: e.target.value }); };

const calculatePrice = () => { const base = 500; // ราคาเริ่มต้น const perKm = 30; // บาทต่อกิโลเมตร const total = base + perKm * Number(form.distance || 0); setPrice(total); };

return ( <div className="min-h-screen flex items-center justify-center bg-gray-100 p-4"> <div className="bg-white shadow-xl rounded-2xl p-6 w-full max-w-md"> <h1 className="text-2xl font-bold mb-4 text-center">🚗 เรียกรถลาก (Towing Car)</h1>

<input
      name="name"
      placeholder="ชื่อผู้เรียก"
      className="w-full border p-2 rounded mb-2"
      onChange={handleChange}
    />
    <input
      name="phone"
      placeholder="เบอร์โทร"
      className="w-full border p-2 rounded mb-2"
      onChange={handleChange}
    />
    <select
      name="vehicle"
      className="w-full border p-2 rounded mb-2"
      onChange={handleChange}
    >
      <option value="">เลือกประเภทรถ</option>
      <option value="car">รถยนต์</option>
      <option value="pickup">กระบะ</option>
      <option value="motorcycle">มอเตอร์ไซค์</option>
    </select>
    <input
      name="distance"
      type="number"
      placeholder="ระยะทาง (กม.)"
      className="w-full border p-2 rounded mb-4"
      onChange={handleChange}
    />

    <button
      onClick={calculatePrice}
      className="w-full bg-blue-600 text-white py-2 rounded-xl"
    >
      คำนวณราคา & เรียกรถ
    </button>

    {price && (
      <div className="mt-4 text-center text-lg font-semibold">
        💰 ราคาโดยประมาณ: {price} บาท
      </div>
    )}
  </div>
</div>

); }
