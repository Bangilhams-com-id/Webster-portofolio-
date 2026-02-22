import React, { useState } from "react"; import { motion } from "framer-motion"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Mail, Github, Linkedin } from "lucide-react";

export default function Portfolio() { const [filter, setFilter] = useState("All");

const projects = [ { title: "Website Portofolio", category: "Website", description: "Website portofolio pribadi dengan tema gelap dan desain modern untuk menampilkan profil dan proyek saya.", }, { title: "Aplikasi To-Do List", category: "Web App", description: "Aplikasi manajemen tugas berbasis React dengan fitur tambah, edit, hapus, dan penyimpanan lokal.", }, { title: "Landing Page Produk", category: "Website", description: "Landing page responsif untuk promosi produk menggunakan HTML, CSS, dan animasi modern.", }, { title: "UI Design Dashboard", category: "UI/UX", description: "Desain antarmuka dashboard admin modern menggunakan Figma dengan fokus pada user experience.", }, { title: "Aplikasi Kasir Sederhana", category: "Desktop", description: "Aplikasi kasir sederhana untuk latihan logika pemrograman dan manajemen data.", }, { title: "REST API Sederhana", category: "Backend", description: "Membangun REST API menggunakan Node.js dan Express untuk sistem manajemen data.", }, ];

const categories = ["All", ...new Set(projects.map((p) => p.category))];

const filteredProjects = filter === "All" ? projects : projects.filter((project) => project.category === filter);

return ( <div className="min-h-screen bg-gradient-to-br from-black via-zinc-900 to-zinc-800 text-white px-6 py-10"> {/* Hero Section */} <section className="max-w-5xl mx-auto text-center py-20"> <motion.img initial={{ opacity: 0, scale: 0.8 }} animate={{ opacity: 1, scale: 1 }} transition={{ duration: 0.6 }} src="/profile.jpg" alt="Foto Profil" className="w-40 h-40 mx-auto rounded-full object-cover border-4 border-indigo-500 shadow-xl mb-6" />

<motion.h1
      initial={{ opacity: 0, y: -20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.6 }}
      className="text-4xl md:text-6xl font-bold mb-6"
    >
      Halo, Saya <span className="text-indigo-500">IBNU PAIS ILHAM SAPUTRA</span>
    </motion.h1>

    <p className="text-zinc-400 max-w-2xl mx-auto text-lg mb-8">
      Saya adalah seorang pelajar atau mahasiswa yang bermimpi menjadi programmer profesional dan terus belajar mengembangkan kemampuan sebagai Developer.
    </p>

    <div className="flex justify-center gap-4">
      <Button className="rounded-2xl px-6">Lihat Proyek</Button>
      <Button variant="outline" className="rounded-2xl px-6">
        Hubungi Saya
      </Button>
    </div>
  </section>

  {/* About Section */}
  <section className="max-w-5xl mx-auto py-16">
    <h2 className="text-3xl font-semibold mb-6">Tentang Saya</h2>
    <p className="text-zinc-400 leading-relaxed">
      Saya adalah seorang Developer yang sedang menempuh pendidikan dan memiliki semangat besar untuk menjadi seorang programmer handal. Saya terus belajar dan mengembangkan kemampuan dalam dunia pemrograman dan teknologi web.
    </p>
  </section>

  {/* Projects Section */}
  <section className="max-w-5xl mx-auto py-16">
    <h2 className="text-3xl font-semibold mb-6">Proyek Saya</h2>

    {/* Filter Buttons */}
    <div className="flex flex-wrap gap-4 mb-10">
      {categories.map((cat) => (
        <Button
          key={cat}
          onClick={() => setFilter(cat)}
          variant={filter === cat ? "default" : "outline"}
          className="rounded-xl"
        >
          {cat}
        </Button>
      ))}
    </div>

    <div className="grid md:grid-cols-3 gap-8">
      {filteredProjects.map((project, index) => (
        <motion.div
          key={index}
          whileHover={{ scale: 1.05 }}
          transition={{ type: "spring", stiffness: 200 }}
          className="group relative"
        >
          <div className="absolute -inset-0.5 bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 rounded-2xl blur opacity-0 group-hover:opacity-70 transition duration-500"></div>

          <Card className="relative bg-zinc-900 border border-zinc-800 rounded-2xl shadow-2xl overflow-hidden">
            <CardContent className="p-6">
              <h3 className="text-xl font-semibold mb-2 group-hover:text-indigo-400 transition">
                {project.title}
              </h3>

              <p className="text-zinc-400 text-sm mb-4 leading-relaxed">
                {project.description}
              </p>

              <div className="flex items-center justify-between">
                <span className="text-xs px-3 py-1 rounded-full bg-zinc-800 text-indigo-400 border border-indigo-500/30">
                  {project.category}
                </span>

                <div className="flex gap-2 opacity-0 group-hover:opacity-100 transition">
                  <Button size="sm" className="rounded-xl text-xs">
                    Demo
                  </Button>
                  <Button size="sm" variant="outline" className="rounded-xl text-xs">
                    Code
                  </Button>
                </div>
              </div>
            </CardContent>
          </Card>
        </motion.div>
      ))}
    </div>
  </section>

  {/* Contact Section */}
  <section className="max-w-5xl mx-auto py-16">
    <h2 className="text-3xl font-semibold mb-6">Kontak</h2>
    <div className="flex gap-6 text-zinc-400">
      <a
        href="mailto:ilhamteran@gmail.com"
        className="flex items-center gap-2 hover:text-white"
      >
        <Mail size={18} /> ilhamteran@gmail.com
      </a>
      <a
        href="#"
        className="flex items-center gap-2 hover:text-white"
      >
        <Github size={18} /> GitHub
      </a>
      <a
        href="#"
        className="flex items-center gap-2 hover:text-white"
      >
        <Linkedin size={18} /> LinkedIn
      </a>
    </div>
  </section>

  <footer className="text-center text-zinc-500 text-sm py-10 border-t border-zinc-800 mt-10">
    © {new Date().getFullYear()} IBNU PAIS ILHAM SAPUTRA. All rights reserved.
  </footer>
</div>

); }
