import { useState, useEffect } from 'react'
import { Search, Filter, Book, ChevronRight, Calendar, FileText, Zap, Link, ThumbsUp, ThumbsDown } from 'lucide-react'
import { Input } from "@/components/ui/input"
import { Button } from "@/components/ui/button"
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog"
import {
  Card,
  CardContent,
  CardDescription,
  CardHeader,
  CardTitle,
} from "@/components/ui/card"
import {
  Select,
  SelectContent,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from "@/components/ui/select"
import { Badge } from "@/components/ui/badge"
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"

export default function AIEnhancedLawRepository() {
  const [selectedLaw, setSelectedLaw] = useState(null)
  const [searchTerm, setSearchTerm] = useState('')
  const [searchSuggestions, setSearchSuggestions] = useState([])

  const laws = [
    { id: 1, title: "UU No. 12 Tahun 2011", description: "Tentang Pembentukan Peraturan Perundang-undangan", category: "Undang-Undang", date: "2011-07-12" },
    { id: 2, title: "UU No. 14 Tahun 2008", description: "Tentang Keterbukaan Informasi Publik", category: "Undang-Undang", date: "2008-04-30" },
    { id: 3, title: "UU No. 39 Tahun 1999", description: "Tentang Hak Asasi Manusia", category: "Undang-Undang", date: "1999-09-23" },
    { id: 4, title: "PP No. 71 Tahun 2019", description: "Tentang Penyelenggaraan Sistem dan Transaksi Elektronik", category: "Peraturan Pemerintah", date: "2019-10-10" },
    { id: 5, title: "Perpres No. 39 Tahun 2019", description: "Tentang Satu Data Indonesia", category: "Peraturan Presiden", date: "2019-06-12" },
  ]

  useEffect(() => {
    if (searchTerm.length > 2) {
      // Simulating AI-powered search suggestions
      const suggestions = laws
        .filter(law => law.title.toLowerCase().includes(searchTerm.toLowerCase()) || 
                       law.description.toLowerCase().includes(searchTerm.toLowerCase()))
        .map(law => law.title)
      setSearchSuggestions(suggestions)
    } else {
      setSearchSuggestions([])
    }
  }, [searchTerm])

  const handleSearch = (term) => {
    setSearchTerm(term)
    // In a real application, this would trigger an API call to search the database
    console.log(`Searching for: ${term}`)
  }

  return (
    <div className="flex flex-col min-h-screen bg-gray-50">
      <header className="bg-gradient-to-r from-red-700 to-red-900 text-white p-6 shadow-lg">
        <div className="container mx-auto flex flex-col md:flex-row justify-between items-center space-y-4 md:space-y-0">
          <h1 className="text-3xl font-bold">Basis Data Hukum Indonesia</h1>
          <div className="flex flex-col items-center space-y-2 w-full md:w-auto">
            <div className="relative w-full md:w-64">
              <Input
                type="search"
                placeholder="Cari peraturan..."
                className="w-full bg-white/10 text-white placeholder-white/70 border-white/20 focus:border-white pr-10"
                value={searchTerm}
                onChange={(e) => setSearchTerm(e.target.value)}
              />
              <Button 
                variant="ghost" 
                className="absolute right-0 top-0 h-full px-3 text-white"
                onClick={() => handleSearch(searchTerm)}
              >
                <Search className="h-4 w-4" />
              </Button>
            </div>
            {searchSuggestions.length > 0 && (
              <Card className="w-full md:w-64 mt-1 absolute top-full left-0 z-10">
                <CardContent className="p-2">
                  {searchSuggestions.map((suggestion, index) => (
                    <Button
                      key={index}
                      variant="ghost"
                      className="w-full justify-start text-sm"
                      onClick={() => handleSearch(suggestion)}
                    >
                      {suggestion}
                    </Button>
                  ))}
                </CardContent>
              </Card>
            )}
          </div>
        </div>
      </header>

      <main className="container mx-auto my-8 px-4 flex flex-col md:flex-row space-y-6 md:space-y-0 md:space-x-8">
        <aside className="w-full md:w-1/4">
          <Card>
            <CardHeader>
              <CardTitle>Filter Peraturan</CardTitle>
              <CardDescription>Pilih jenis peraturan</CardDescription>
            </CardHeader>
            <CardContent>
              <Select>
                <SelectTrigger className="w-full">
                  <SelectValue placeholder="Pilih jenis peraturan" />
                </SelectTrigger>
                <SelectContent>
                  <SelectItem value="all">Semua Peraturan</SelectItem>
                  <SelectItem value="uu">Undang-Undang</SelectItem>
                  <SelectItem value="pp">Peraturan Pemerintah</SelectItem>
                  <SelectItem value="perpres">Peraturan Presiden</SelectItem>
                </SelectContent>
              </Select>
            </CardContent>
          </Card>
        </aside>

        <section className="w-full md:w-3/4">
          <h2 className="text-2xl font-bold mb-6">Daftar Peraturan Terbaru</h2>
          <div className="grid gap-6 md:grid-cols-2">
            {laws.map((law) => (
              <Card key={law.id} className="transition-shadow hover:shadow-md">
                <CardHeader>
                  <CardTitle>{law.title}</CardTitle>
                  <CardDescription>{law.description}</CardDescription>
                </CardHeader>
                <CardContent>
                  <div className="flex justify-between items-center text-sm text-gray-500 mb-4">
                    <span className="flex items-center">
                      <FileText className="h-4 w-4 mr-1" />
                      {law.category}
                    </span>
                    <span className="flex items-center">
                      <Calendar className="h-4 w-4 mr-1" />
                      {law.date}
                    </span>
                  </div>
                  <Dialog>
                    <DialogTrigger asChild>
                      <Button variant="outline" className="w-full" onClick={() => setSelectedLaw(law)}>
                        Lihat Detail
                        <ChevronRight className="h-4 w-4 ml-2" />
                      </Button>
                    </DialogTrigger>
                    <DialogContent className="max-w-4xl max-h-[80vh] overflow-y-auto">
                      <DialogHeader>
                        <DialogTitle>{law.title}</DialogTitle>
                        <DialogDescription>{law.description}</DialogDescription>
                      </DialogHeader>
                      <Tabs defaultValue="ringkasan" className="mt-4">
                        <TabsList>
                          <TabsTrigger value="ringkasan">Ringkasan AI</TabsTrigger>
                          <TabsTrigger value="lengkap">Teks Lengkap</TabsTrigger>
                          <TabsTrigger value="terkait">Peraturan Terkait</TabsTrigger>
                        </TabsList>
                        <TabsContent value="ringkasan">
                          <Card>
                            <CardHeader>
                              <CardTitle className="text-lg">Ringkasan AI</CardTitle>
                              <CardDescription>Dihasilkan oleh AI untuk pemahaman cepat</CardDescription>
                            </CardHeader>
                            <CardContent>
                              <p>
                                Ringkasan AI dari {law.title} akan ditampilkan di sini. Ringkasan ini akan mencakup
                                poin-poin utama dari undang-undang, tujuannya, dan implikasi pentingnya.
                              </p>
                              <div className="flex items-center justify-end space-x-2 mt-4">
                                <span className="text-sm text-gray-500">Apakah ringkasan ini membantu?</span>
                                <Button variant="outline" size="sm">
                                  <ThumbsUp className="h-4 w-4 mr-1" />
                                  Ya
                                </Button>
                                <Button variant="outline" size="sm">
                                  <ThumbsDown className="h-4 w-4 mr-1" />
                                  Tidak
                                </Button>
                              </div>
                            </CardContent>
                          </Card>
                        </TabsContent>
                        <TabsContent value="lengkap">
                          <Card>
                            <CardHeader>
                              <CardTitle className="text-lg">Teks Lengkap</CardTitle>
                            </CardHeader>
                            <CardContent>
                              <p>
                                Teks lengkap dari {law.title} akan ditampilkan di sini, termasuk semua pasal,
                                bab, dan bagian-bagian lainnya dari undang-undang.
                              </p>
                            </CardContent>
                          </Card>
                        </TabsContent>
                        <TabsContent value="terkait">
                          <Card>
                            <CardHeader>
                              <CardTitle className="text-lg">Peraturan Terkait</CardTitle>
                              <CardDescription>Direkomendasikan oleh AI</CardDescription>
                            </CardHeader>
                            <CardContent>
                              <ul className="space-y-2">
                                <li>
                                  <Link className="text-blue-600 hover:underline flex items-center">
                                    <Link className="h-4 w-4 mr-2" />
                                    UU No. 10 Tahun 2004 (Dicabut)
                                  </Link>
                                </li>
                                <li>
                                  <Link className="text-blue-600 hover:underline flex items-center">
                                    <Link className="h-4 w-4 mr-2" />
                                    PP No. 59 Tahun 2015
                                  </Link>
                                </li>
                              </ul>
                            </CardContent>
                          </Card>
                        </TabsContent>
                      </Tabs>
                    </DialogContent>
                  </Dialog>
                </CardContent>
              </Card>
            ))}
          </div>
        </section>
      </main>

      <footer className="bg-gray-200 text-center p-6 mt-auto">
        <p className="text-gray-600">&copy; 2023 Basis Data Hukum Indonesia. Hak Cipta Dilindungi.</p>
        <p className="text-sm text-gray-500 mt-2">
          Dikembangkan oleh Kementerian Hukum dan Hak Asasi Manusia Republik Indonesia
        </p>
        <Badge variant="outline" className="mt-2">
          <Zap className="h-4 w-4 mr-1" />
          Diperkaya dengan AI
        </Badge>
      </footer>
    </div>
  )
}
