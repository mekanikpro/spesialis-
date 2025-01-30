import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Label } from "@/components/ui/label";
import { motion } from "framer-motion";

const HomePage = () => {
  const [formData, setFormData] = useState({
    brand: "",
    location: "",
    schedule: "",
  });

  const handleChange = (e) => {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  };

  const handleSubmit = () => {
    if (!formData.brand || !formData.location || !formData.schedule) {
      alert("Harap isi semua kolom sebelum melakukan pemesanan.");
      return;
    }

    const whatsappMessage = `Halo, saya ingin memesan layanan gurah mesin.\n\nNama Merek Mobil: ${formData.brand}\nAlamat Lokasi: ${formData.location}\nJadwal Layanan: ${formData.schedule}`;
    const whatsappUrl = `https://wa.me/6288220211486?text=${encodeURIComponent(
      whatsappMessage
    )}`;
    window.open(whatsappUrl, "_blank");
  };

  return (
    <div className="min-h-screen bg-gradient-to-r from-blue-500 to-green-400 flex flex-col items-center p-6 text-white">
      <motion.h1
        className="text-4xl font-bold mt-10 drop-shadow-lg text-center"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
      >
        Selamat Datang di Bisnis Spesialis Gurah Mesin Mobil Pengalaman dan
        Terpercaya Aman Dijamin
      </motion.h1>
      <p className="mt-4 text-lg text-center max-w-2xl drop-shadow-md">
        Kami menyediakan layanan terbaik untuk kebutuhan Anda. Hubungi kami
        untuk informasi lebih lanjut.
      </p>

      {/* Tombol Hubungi Kami */}
      <Button
        className="mt-4 bg-yellow-500 hover:bg-yellow-600 text-gray-800 font-semibold rounded-xl shadow-md px-6 py-3"
        onClick={() => window.open("https://wa.me/6288220211486", "_blank")}
      >
        Hubungi Kami di WhatsApp
      </Button>

      <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mt-10">
        <Card className="shadow-xl rounded-2xl p-6 bg-white text-gray-800">
          <CardContent>
            <h2 className="text-xl font-semibold">
              Manfaat Proses Gurah Mesin Mobil Bisa Dibuktikan Hasilnya Aman
            </h2>
            <p className="mt-2">
              Proses gurah mesin mobil membantu membersihkan komponen mesin dari
              kotoran dan endapan yang mengganggu kinerja.
            </p>
          </CardContent>
        </Card>
        <Card className="shadow-xl rounded-2xl p-6 bg-white text-gray-800">
          <CardContent>
            <h2 className="text-xl font-semibold">
              Proses Gurah Mesin Menggunakan Cairan Carbon Cleaner Water Based
            </h2>
            <p className="mt-2">
              Jika mobil terasa berat, boros BBM, suara kasar, atau tenaga
              menurun, ini bisa menjadi solusi yang efektif dan terjangkau.
            </p>
          </CardContent>
        </Card>
        <Card className="shadow-xl rounded-2xl p-6 bg-white text-gray-800">
          <CardContent>
            <h2 className="text-xl font-semibold">
              Kapan Waktu Gurah Mesin Mobil Terbaik
            </h2>
            <p className="mt-2">
              Setelah 2x ganti oli atau 10.000 KM adalah waktu terbaik untuk
              melakukan gurah mesin agar ruang bakar kembali bersih seperti
              baru.
            </p>
          </CardContent>
        </Card>
      </div>

      <div className="text-center mt-8">
        <h3 className="text-xl font-semibold drop-shadow-md">Alamat Kami</h3>
        <p className="">
          Jl. Anggrek No.7, Blotan, Wedomartani, Kec. Ngemplak, Kabupaten
          Sleman, Daerah Istimewa Yogyakarta 55584
        </p>
        <p className="">
          Telepon:{" "}
          <a
            href="https://wa.me/6288220211486"
            className="text-yellow-300 underline"
          >
            0882-2021-1486 (WhatsApp)
          </a>
        </p>
      </div>

      <div className="bg-white p-6 rounded-xl shadow-xl mt-8 w-full max-w-md text-gray-800">
        <h3 className="text-lg font-semibold mb-4">Formulir Pemesanan</h3>
        <Label>Nama Merek Mobil</Label>
        <Input
          name="brand"
          value={formData.brand}
          onChange={handleChange}
          className="mb-4 border border-gray-300 p-2 rounded-md"
        />
        <Label>Alamat Lokasi</Label>
        <Input
          name="location"
          value={formData.location}
          onChange={handleChange}
          className="mb-4 border border-gray-300 p-2 rounded-md"
        />
        <Label>Jadwal Layanan</Label>
        <Input
          name="schedule"
          type="date"
          value={formData.schedule}
          onChange={handleChange}
          className="mb-4 border border-gray-300 p-2 rounded-md"
        />
        <Button
          onClick={handleSubmit}
          className="w-full bg-yellow-400 text-gray-800 font-semibold rounded-xl shadow-md hover:bg-yellow-500"
        >
          Pesan Sekarang
        </Button>
      </div>
    </div>
  );
};

export default HomePage;

