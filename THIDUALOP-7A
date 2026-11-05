import React, { useState, useMemo, useEffect } from 'react';
import { 
    User, BookOpen, AlertTriangle, CheckCircle, 
    XCircle, BarChart3, ShieldAlert, Users, 
    Smartphone, Search, Filter, ShieldCheck,
    LogOut, PlusCircle, CheckSquare, X, Download,
    TrendingUp, TrendingDown, Minus, Calendar
} from 'lucide-react';

// --- DATA: STUDENTS ---
const initialStudents = [
    { id: 'HS01', name: 'Nguyễn Gia An', group: 1 }, { id: 'HS02', name: 'Phạm Quốc An', group: 1 },
    { id: 'HS03', name: 'Vàng Tiến An', group: 1 }, { id: 'HS04', name: 'Nguyễn Thế Anh', group: 1 },
    { id: 'HS05', name: 'Nguyễn Thị Quỳnh Anh', group: 1 }, { id: 'HS06', name: 'Phan Thị Tú Anh', group: 1 },
    { id: 'HS07', name: 'Nguyễn Viết Bằng', group: 1 }, { id: 'HS08', name: 'Cà Gia Bảo', group: 1 },
    { id: 'HS09', name: 'Nguyễn Thị Thái Bảo', group: 1 }, { id: 'HS10', name: 'Nguyễn Ngọc Minh Châu', group: 1 },
    { id: 'HS11', name: 'Hà Đặng Quỳnh Chi', group: 2 }, { id: 'HS12', name: 'Lò Diệp Chi', group: 2 },
    { id: 'HS13', name: 'Lò Cẩm Chi', group: 2 }, { id: 'HS14', name: 'Trần Khánh Chi', group: 2 },
    { id: 'HS15', name: 'Nguyễn Ngọc Diệp', group: 2 }, { id: 'HS16', name: 'Trần Đăng Thành Đạt', group: 2 },
    { id: 'HS17', name: 'Hà Bảo Hân', group: 2 }, { id: 'HS18', name: 'Hoàng Ngọc Hân', group: 2 },
    { id: 'HS19', name: 'Nguyễn Ngọc Hiếu', group: 2 }, { id: 'HS20', name: 'Nguyễn Thế Hưng', group: 3 },
    { id: 'HS21', name: 'Nguyễn Mai Hương', group: 3 }, { id: 'HS22', name: 'Lê Bảo Khánh', group: 3 },
    { id: 'HS23', name: 'Nguyễn Đăng Khoa', group: 3 }, { id: 'HS24', name: 'Đặng Tuệ Lâm', group: 3 },
    { id: 'HS25', name: 'Hoàng Nhật Linh', group: 3 }, { id: 'HS26', name: 'Nguyễn Đức Mạnh', group: 3 },
    { id: 'HS27', name: 'Lê Hiểu Minh', group: 3 }, { id: 'HS28', name: 'Nguyễn Tạ Thu Minh', group: 3 },
    { id: 'HS29', name: 'Phạm Thảo Nguyên', group: 4 }, { id: 'HS30', name: 'Hà Hồng Phúc', group: 4 },
    { id: 'HS31', name: 'Bùi Lan Phương', group: 4 }, { id: 'HS32', name: 'Nguyễn Trung Quân', group: 4 },
    { id: 'HS33', name: 'Quàng Thị Bảo Trâm', group: 4 }, { id: 'HS34', name: 'Hoàng Bùi Bảo Trang', group: 4 },
    { id: 'HS35', name: 'Đoàn Thanh Trúc', group: 4 }, { id: 'HS36', name: 'Nguyễn Khắc Vinh', group: 4 },
    { id: 'HS37', name: 'Bùi Quang Vương', group: 4 }
];

// --- DATA: 29 CRITERIA ---
const categories = [
    { id: 'I', name: 'Chuyên cần và giờ giấc' },
    { id: 'II', name: 'Trang phục và tác phong' },
    { id: 'III', name: 'Ý thức học tập' },
    { id: 'IV', name: 'Điện thoại' },
    { id: 'V', name: 'Hoạt động tập thể và tinh thần trách nhiệm' },
    { id: 'VI', name: 'Vệ sinh và bảo vệ của công' },
    { id: 'VII', name: 'Đạo đức và ứng xử' }
];

const criteriaList = [
    { id: 1, categoryId: 'I', name: 'Đi học muộn', point: -3 },
    { id: 2, categoryId: 'I', name: 'Nghỉ học không phép', point: -10 },
    { id: 3, categoryId: 'I', name: 'Tự ý ra khỏi lớp, bỏ vị trí khi chưa được phép', point: -10 },
    { id: 4, categoryId: 'I', name: 'Đi học đầy đủ, đúng giờ cả tháng', point: 5 },
    { id: 5, categoryId: 'II', name: 'Mặc đồng phục không đúng quy định', point: -5 },
    { id: 6, categoryId: 'II', name: 'Thiếu khăn quàng đỏ, phù hiệu theo quy định', point: -2 },
    { id: 7, categoryId: 'II', name: 'Đi giày dép không đúng quy định', point: -2 },
    { id: 8, categoryId: 'II', name: 'Đầu tóc, diện mạo không đúng nội quy', point: -5 },
    { id: 9, categoryId: 'III', name: 'Quên SGK, vở ghi, đồ dùng học tập', point: -3 },
    { id: 10, categoryId: 'III', name: 'Không làm bài tập, không học bài cũ', point: -5 },
    { id: 11, categoryId: 'III', name: 'Nói chuyện riêng, làm việc riêng, quay cóp, ngủ gật', point: -5 },
    { id: 12, categoryId: 'III', name: 'Đạt điểm 9 hoặc 10 trong bài kiểm tra', point: 3 },
    { id: 13, categoryId: 'III', name: 'Được giáo viên bộ môn khen ngợi', point: 3 },
    { id: 14, categoryId: 'IV', name: 'Tự ý mang điện thoại đến lớp khi chưa được phép', point: -50 },
    { id: 15, categoryId: 'IV', name: 'Phát hiện và báo cáo trung thực bạn tự ý mang ĐT', point: 20 },
    { id: 16, categoryId: 'V', name: 'Không nghiêm túc trong 15 phút đầu giờ', point: -3 },
    { id: 17, categoryId: 'V', name: 'Mất trật tự, thiếu nghiêm túc trong giờ học, chào cờ', point: -5 },
    { id: 18, categoryId: 'V', name: 'Không vệ sinh sau chào cờ, vứt rác, quên ghế', point: -3 },
    { id: 19, categoryId: 'V', name: 'Trốn hoặc tập thể dục giữa giờ không nghiêm túc', point: -3 },
    { id: 20, categoryId: 'V', name: 'Không thực hiện nhiệm vụ ngoại khóa, sự kiện', point: -7 },
    { id: 21, categoryId: 'V', name: 'Tích cực tham gia văn nghệ, thể thao, phong trào', point: 7 },
    { id: 22, categoryId: 'V', name: 'Ban cán sự hoàn thành tốt nhiệm vụ', point: 5 },
    { id: 23, categoryId: 'VI', name: 'Tổ không hoàn thành nhiệm vụ trực nhật (trừ cả tổ)', point: -5, isGroup: true },
    { id: 24, categoryId: 'VI', name: 'Ăn quà vặt sai quy định, xả rác', point: -5 },
    { id: 25, categoryId: 'VI', name: 'Vẽ bậy, làm hỏng, sử dụng lãng phí CSVC', point: -10 },
    { id: 26, categoryId: 'VII', name: 'Nói tục, chửi thề, giao tiếp thiếu văn minh', point: -7 },
    { id: 27, categoryId: 'VII', name: 'Có lời nói, hành vi thiếu tôn trọng thầy cô, nhân viên', point: -20 },
    { id: 28, categoryId: 'VII', name: 'Đánh nhau, đe dọa, gây gổ, cổ vũ bạo lực', point: -30 },
    { id: 29, categoryId: 'VII', name: 'Nhặt được của rơi trả lại, giúp đỡ bạn, làm việc tốt', point: 7 },
    { id: 30, categoryId: 'VII', name: 'Khen thưởng đột xuất', point: 10 }
];

// --- HELPER FUNCTIONS ---
const getRanking = (score) => {
    if (score >= 90) return { label: 'Tốt', color: 'text-green-600', bg: 'bg-green-100' };
    if (score >= 75) return { label: 'Khá', color: 'text-blue-600', bg: 'bg-blue-100' };
    if (score >= 60) return { label: 'Trung bình', color: 'text-yellow-600', bg: 'bg-yellow-100' };
    return { label: 'Chưa đạt', color: 'text-red-600', bg: 'bg-red-100' };
};

const getCriterionStr = (id) => {
    const c = criteriaList.find(x => x.id === id);
    return c ? `${c.name} (${c.point > 0 ? '+' : ''}${c.point})` : 'Không xác định';
};

// --- MAIN APP COMPONENT ---
export default function App() {
    const [students, setStudents] = useState(initialStudents);
    const [role, setRole] = useState(null); // 'GVCN', 'CAN_SU', 'SAO_DO', 'TO_TRUONG'
    const [view, setView] = useState('DASHBOARD');
    
    // Fake db for incidents
    const [incidents, setIncidents] = useState([
        {
            id: 'INC1', studentId: 'HS05', criteriaId: 1, point: -3, 
            reporterRole: 'SAO_DO', reporterName: 'Đội Cờ Đỏ', date: '2026-10-25',
            status: 'confirmed', notes: 'Đi muộn 15p (Tháng trước)'
        },
        {
            id: 'INC2', studentId: 'HS12', criteriaId: 14, point: -50, 
            reporterRole: 'GVCN', reporterName: 'Cô Lan', date: '2026-11-02',
            status: 'pending', notes: 'Sử dụng điện thoại trong giờ Toán'
        },
        {
            id: 'INC3', studentId: 'HS05', criteriaId: 12, point: 3, 
            reporterRole: 'GVCN', reporterName: 'Cô Lan', date: '2026-11-04',
            status: 'confirmed', notes: 'Điểm 10 Toán'
        },
        {
            id: 'INC4', studentId: 'HS01', criteriaId: 12, point: 3, 
            reporterRole: 'GVCN', reporterName: 'Cô Lan', date: '2026-10-10',
            status: 'confirmed', notes: 'Điểm 9 Văn (Tháng trước)'
        },
        {
            id: 'INC5', studentId: 'HS01', criteriaId: 3, point: -10, 
            reporterRole: 'GVCN', reporterName: 'Cô Lan', date: '2026-11-05',
            status: 'confirmed', notes: 'Bỏ vị trí'
        }
    ]);

    // Modal state for recording
    const [isRecordModalOpen, setIsRecordModalOpen] = useState(false);

    // Filter state for Reports
    const [reportWeek, setReportWeek] = useState(1);

    const handleLogin = (selectedRole) => {
        setRole(selectedRole);
        setView(selectedRole === 'GVCN' ? 'APPROVAL' : 'RECORD');
    };

    const handleLogout = () => {
        setRole(null);
        setView('DASHBOARD');
    };

    return (
        <div className="min-h-screen bg-gradient-to-br from-blue-50 via-slate-50 to-indigo-50 font-sans text-slate-800">
            {/* HEADER */}
            <header className="bg-gradient-to-r from-blue-700 via-blue-600 to-indigo-700 text-white shadow-lg sticky top-0 z-40">
                <div className="max-w-6xl mx-auto px-4 py-3 flex justify-between items-center">
                    <div className="flex items-center gap-3">
                        <div className="bg-white/20 p-2 rounded-lg backdrop-blur-sm shadow-sm">
                            <BookOpen className="w-6 h-6 text-white" />
                        </div>
                        <h1 className="text-xl md:text-2xl font-extrabold tracking-tight drop-shadow-sm">Sổ Thi Đua Lớp 7</h1>
                    </div>
                    {role ? (
                        <div className="flex items-center gap-4">
                            <span className="text-sm font-semibold bg-white/20 backdrop-blur-md border border-white/30 shadow-sm px-4 py-1.5 rounded-full flex items-center gap-2 transition hover:bg-white/30">
                                <User className="w-4 h-4"/>
                                {role === 'GVCN' ? 'Giáo viên CN' : 
                                 role === 'CAN_SU' ? 'Cán sự lớp' : 
                                 role === 'SAO_DO' ? 'Sao đỏ' : 'Tổ trưởng'}
                            </span>
                            <button onClick={handleLogout} className="bg-red-500/80 hover:bg-red-500 text-white p-2 rounded-full transition-all shadow-sm hover:shadow-md hover:-translate-y-0.5">
                                <LogOut className="w-5 h-5" />
                            </button>
                        </div>
                    ) : (
                        <div className="hidden md:flex text-sm font-medium opacity-90 bg-white/10 px-3 py-1 rounded-full border border-white/20">Hệ thống đánh giá điểm chuẩn</div>
                    )}
                </div>
            </header>

            {/* MAIN CONTENT */}
            <main className="max-w-6xl mx-auto px-4 py-8">
                {!role ? (
                    <LoginScreen onLogin={handleLogin} />
                ) : (
                    <div className="flex flex-col md:flex-row gap-6">
                        {/* SIDEBAR */}
                        <div className="w-full md:w-64 shrink-0">
                            <nav className="flex md:flex-col gap-2 bg-white/80 backdrop-blur-xl p-3 rounded-2xl shadow-lg border border-white/50 overflow-x-auto sticky top-24">
                                {(role === 'GVCN' || role === 'CAN_SU' || role === 'SAO_DO' || role === 'TO_TRUONG') && (
                                    <button 
                                        onClick={() => setIsRecordModalOpen(true)}
                                        className="flex items-center justify-center gap-2 px-4 py-3.5 mb-2 bg-gradient-to-r from-blue-600 to-indigo-600 text-white rounded-xl hover:shadow-lg hover:from-blue-500 hover:to-indigo-500 transition-all transform hover:-translate-y-0.5 w-full whitespace-nowrap border border-blue-500/30 font-bold shadow-md"
                                    >
                                        <PlusCircle className="w-5 h-5" />
                                        <span>Ghi nhận mới</span>
                                    </button>
                                )}
                                
                                {role === 'GVCN' && (
                                    <NavButton 
                                        active={view === 'APPROVAL'} onClick={() => setView('APPROVAL')} 
                                        icon={<ShieldCheck />} label="Duyệt vi phạm" 
                                        badge={incidents.filter(i => i.status === 'pending').length}
                                    />
                                )}
                                
                                {role === 'GVCN' && (
                                    <NavButton 
                                        active={view === 'CLASS_MANAGE'} onClick={() => setView('CLASS_MANAGE')} 
                                        icon={<Users />} label="Quản lý Tổ & Cán sự" 
                                    />
                                )}
                                
                                <NavButton 
                                    active={view === 'REPORT'} onClick={() => setView('REPORT')} 
                                    icon={<BarChart3 />} label="Bảng điểm Tuần/Tháng" 
                                />
                                
                                <NavButton 
                                    active={view === 'HISTORY'} onClick={() => setView('HISTORY')} 
                                    icon={<CheckSquare />} label="Lịch sử sự việc" 
                                />

                                <NavButton 
                                    active={view === 'CRITERIA'} onClick={() => setView('CRITERIA')} 
                                    icon={<AlertTriangle />} label="Quy chế (30 Tiêu chí)" 
                                />
                            </nav>
                        </div>

                        {/* CONTENT AREA */}
                        <div className="flex-1 bg-white/90 backdrop-blur-xl rounded-2xl shadow-lg border border-white/60 p-4 md:p-6 min-h-[500px]">
                            {view === 'APPROVAL' && role === 'GVCN' && (
                                <ApprovalView incidents={incidents} setIncidents={setIncidents} students={students} />
                            )}
                            {view === 'REPORT' && (
                                <ReportView incidents={incidents} students={students} />
                            )}
                            {view === 'HISTORY' && (
                                <HistoryView incidents={incidents} role={role} students={students} />
                            )}
                            {view === 'CRITERIA' && (
                                <CriteriaView />
                            )}
                            {view === 'CLASS_MANAGE' && role === 'GVCN' && (
                                <ClassManageView students={students} setStudents={setStudents} />
                            )}
                        </div>
                    </div>
                )}
            </main>

            {/* RECORD MODAL */}
            {isRecordModalOpen && (
                <RecordModal 
                    role={role} 
                    students={students}
                    onClose={() => setIsRecordModalOpen(false)} 
                    onSave={(newIncident) => {
                        setIncidents([...incidents, newIncident]);
                        setIsRecordModalOpen(false);
                    }}
                />
            )}
        </div>
    );
}

// --- SUB-COMPONENTS ---

function LoginScreen({ onLogin }) {
    return (
        <div className="max-w-md mx-auto mt-16 bg-white/90 backdrop-blur-xl p-8 rounded-3xl shadow-2xl border border-white/60 text-center transform transition-all hover:scale-[1.01] duration-300">
            <div className="w-20 h-20 bg-gradient-to-br from-blue-100 to-indigo-100 text-blue-600 rounded-2xl shadow-inner flex items-center justify-center mx-auto mb-6 rotate-3">
                <ShieldAlert className="w-10 h-10 transform -rotate-3" />
            </div>
            <h2 className="text-3xl font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-blue-700 to-indigo-800 mb-3">Đăng nhập Hệ thống</h2>
            <p className="text-gray-500 mb-8 text-sm font-medium">Chọn vai trò của bạn để truy cập sổ thi đua. GVCN có quyền duyệt cuối cùng.</p>
            
            <div className="grid gap-3.5">
                <button onClick={() => onLogin('GVCN')} className="group relative overflow-hidden p-3.5 bg-white text-blue-700 hover:text-white rounded-xl font-bold shadow-sm border border-blue-100 transition-all flex items-center justify-center gap-2 hover:shadow-md">
                    <div className="absolute inset-0 w-0 bg-gradient-to-r from-blue-600 to-indigo-600 transition-all duration-300 ease-out group-hover:w-full -z-10"></div>
                    <ShieldCheck className="w-5 h-5 z-10"/> <span className="z-10">Giáo viên chủ nhiệm</span>
                </button>
                <button onClick={() => onLogin('CAN_SU')} className="group relative overflow-hidden p-3.5 bg-white text-emerald-700 hover:text-white rounded-xl font-bold shadow-sm border border-emerald-100 transition-all flex items-center justify-center gap-2 hover:shadow-md">
                    <div className="absolute inset-0 w-0 bg-gradient-to-r from-emerald-500 to-teal-500 transition-all duration-300 ease-out group-hover:w-full -z-10"></div>
                    <BookOpen className="w-5 h-5 z-10"/> <span className="z-10">Sổ Đầu Bài (Cán sự lớp)</span>
                </button>
                <button onClick={() => onLogin('SAO_DO')} className="group relative overflow-hidden p-3.5 bg-white text-rose-700 hover:text-white rounded-xl font-bold shadow-sm border border-rose-100 transition-all flex items-center justify-center gap-2 hover:shadow-md">
                    <div className="absolute inset-0 w-0 bg-gradient-to-r from-rose-500 to-pink-500 transition-all duration-300 ease-out group-hover:w-full -z-10"></div>
                    <AlertTriangle className="w-5 h-5 z-10"/> <span className="z-10">Sổ Sao Đỏ</span>
                </button>
                <button onClick={() => onLogin('TO_TRUONG')} className="group relative overflow-hidden p-3.5 bg-white text-purple-700 hover:text-white rounded-xl font-bold shadow-sm border border-purple-100 transition-all flex items-center justify-center gap-2 hover:shadow-md">
                    <div className="absolute inset-0 w-0 bg-gradient-to-r from-purple-500 to-violet-500 transition-all duration-300 ease-out group-hover:w-full -z-10"></div>
                    <Users className="w-5 h-5 z-10"/> <span className="z-10">Sổ Tổ Trưởng</span>
                </button>
            </div>
        </div>
    );
}

function NavButton({ active, onClick, icon, label, badge }) {
    return (
        <button 
            onClick={onClick}
            className={`flex items-center justify-between px-4 py-3.5 rounded-xl transition-all duration-200 w-full ${
                active ? 'bg-gradient-to-r from-blue-50 to-indigo-50/50 text-blue-700 font-bold border-l-4 border-blue-600 shadow-sm' : 'text-gray-600 font-medium hover:bg-gray-50 hover:text-indigo-600 border-l-4 border-transparent'
            }`}
        >
            <div className="flex items-center gap-3">
                {React.cloneElement(icon, { className: `w-5 h-5 ${active ? 'text-blue-600' : 'text-gray-400'}` })}
                <span className="whitespace-nowrap">{label}</span>
            </div>
            {badge > 0 && (
                <span className="bg-gradient-to-r from-red-500 to-rose-500 text-white text-xs font-bold px-2 py-0.5 rounded-full shadow-sm">
                    {badge}
                </span>
            )}
        </button>
    );
}

// --- VIEWS ---

function ApprovalView({ incidents, setIncidents, students }) {
    const pending = incidents.filter(i => i.status === 'pending');

    const handleAction = (id, status) => {
        setIncidents(incidents.map(inc => inc.id === id ? { ...inc, status } : inc));
    };

    if (pending.length === 0) {
        return (
            <div className="flex flex-col items-center justify-center h-64 text-gray-400">
                <CheckCircle className="w-16 h-16 mb-4 text-gray-200" />
                <p className="text-lg">Tuyệt vời! Không có sự việc nào cần duyệt.</p>
            </div>
        );
    }

    return (
        <div>
            <h2 className="text-xl font-bold mb-4 flex items-center gap-2">
                <ShieldCheck className="text-blue-600" /> Chờ GVCN Xác nhận
            </h2>
            <div className="space-y-4">
                {pending.map(inc => {
                    const student = students.find(s => s.id === inc.studentId);
                    const isGroup = inc.criteriaId === 23; // Special case: Tổ
                    const targetName = isGroup ? `Tổ ${inc.groupId}` : student?.name;
                    
                    return (
                        <div key={inc.id} className="bg-white border border-yellow-200 p-4 rounded-xl shadow-sm flex flex-col md:flex-row justify-between gap-4 items-start md:items-center">
                            <div>
                                <div className="flex items-center gap-2 mb-1">
                                    <span className="font-bold text-lg text-gray-800">{targetName}</span>
                                    {isGroup && <span className="text-xs bg-purple-100 text-purple-700 px-2 py-0.5 rounded font-bold">CẢ TỔ</span>}
                                    {student?.title && !isGroup && <span className="text-xs bg-blue-100 text-blue-700 px-2 py-0.5 rounded font-bold">{student.title}</span>}
                                    <span className="text-sm text-gray-500">({inc.date})</span>
                                </div>
                                <div className="text-sm font-medium text-red-600">
                                    Lỗi: {getCriterionStr(inc.criteriaId)}
                                </div>
                                {inc.criteriaId === 15 && (
                                    <div className="text-xs bg-blue-50 text-blue-700 p-2 rounded mt-1 border border-blue-100">
                                        <ShieldCheck className="w-3 h-3 inline mr-1" />
                                        Bảo mật danh tính. Chỉ GVCN thấy. Báo cáo: {inc.reportedStudentId ? students.find(s => s.id === inc.reportedStudentId)?.name : 'Không rõ'} vi phạm.
                                    </div>
                                )}
                                <div className="text-sm text-gray-600 mt-1">
                                    Ghi nhận bởi: <span className="font-semibold">{inc.reporterRole}</span> - {inc.notes}
                                </div>
                            </div>
                            <div className="flex gap-2 shrink-0 w-full md:w-auto">
                                <button 
                                    onClick={() => handleAction(inc.id, 'confirmed')}
                                    className="flex-1 md:flex-none flex items-center justify-center gap-1 bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg font-medium transition"
                                >
                                    <CheckCircle className="w-4 h-4"/> Duyệt
                                </button>
                                <button 
                                    onClick={() => handleAction(inc.id, 'rejected')}
                                    className="flex-1 md:flex-none flex items-center justify-center gap-1 bg-red-100 hover:bg-red-200 text-red-700 px-4 py-2 rounded-lg font-medium transition"
                                >
                                    <XCircle className="w-4 h-4"/> Từ chối
                                </button>
                            </div>
                        </div>
                    );
                })}
            </div>
        </div>
    );
}

function ReportView({ incidents, students }) {
    const today = new Date();
    const currentMonthStr = today.toISOString().substring(0, 7);

    const [filterType, setFilterType] = useState('month'); // 'week' or 'month'
    const [selectedMonth, setSelectedMonth] = useState(currentMonthStr);

    // Available months from incidents
    const availableMonths = useMemo(() => {
        const months = new Set(incidents.map(i => i.date.substring(0, 7)));
        months.add(currentMonthStr);
        return Array.from(months).sort().reverse();
    }, [incidents, currentMonthStr]);

    const getScoreForPeriod = (student, filterVal, isWeek, confirmedIncidents) => {
        let score = 100;
        let plus = 0;
        let minus = 0;
        let phoneViolations = 0;

        let periodIncidents = [];
        if (isWeek) {
            // Simplified week: just past 7 days
            const weekAgo = new Date();
            weekAgo.setDate(weekAgo.getDate() - 7);
            periodIncidents = confirmedIncidents.filter(i => new Date(i.date) >= weekAgo);
        } else {
            // filterVal is YYYY-MM
            periodIncidents = confirmedIncidents.filter(i => i.date.startsWith(filterVal));
        }

        const personal = periodIncidents.filter(i => i.studentId === student.id);
        personal.forEach(inc => {
            if (inc.point > 0) plus += inc.point;
            else minus += Math.abs(inc.point);
            if (inc.criteriaId === 14) phoneViolations++;
        });

        const groupIncidents = periodIncidents.filter(i => i.criteriaId === 23 && i.groupId === student.group);
        groupIncidents.forEach(inc => {
            minus += Math.abs(inc.point);
        });

        score = score + plus - minus;
        return { score, plus, minus, phoneViolations };
    };

    // Tự động tính điểm
    const calculateScores = () => {
        const confirmedIncidents = incidents.filter(i => i.status === 'confirmed');
        
        let report = students.map(st => {
            const data = getScoreForPeriod(st, selectedMonth, filterType === 'week', confirmedIncidents);
            
            // Calculate previous month score for trend (only if filter is month)
            let prevData = { score: 100 }; // Default base
            if (filterType === 'month') {
                const [year, month] = selectedMonth.split('-');
                const prevDate = new Date(year, parseInt(month) - 2, 1);
                const prevMonthStr = prevDate.toISOString().substring(0, 7);
                prevData = getScoreForPeriod(st, prevMonthStr, false, confirmedIncidents);
            }

            let trendVal = data.score - prevData.score;
            let trendText = "Giữ phong độ";
            let trendColor = "text-gray-500";
            if (trendVal > 0) {
                trendText = `Tiến bộ (+${trendVal})`;
                trendColor = "text-green-600";
            } else if (trendVal < 0) {
                trendText = `Sa sút (${trendVal})`;
                trendColor = "text-red-600";
            }

            return {
                ...st, ...data, rank: getRanking(data.score),
                trendText, trendVal, trendColor
            };
        });

        // Sắp xếp theo điểm giảm dần
        report.sort((a, b) => b.score - a.score);

        // Xếp hạng (Xử lý đồng hạng)
        let currentRank = 1;
        let previousScore = null;
        report.forEach((st, idx) => {
            if (previousScore !== null && st.score < previousScore) {
                currentRank = idx + 1;
            }
            st.position = currentRank;
            previousScore = st.score;
        });

        return report;
    };

    const reportData = calculateScores();

    const handleExportExcel = () => {
        const headers = ['Hang', 'STT', 'Ho va ten', 'To', 'Diem cong', 'Diem tru', 'Loi dien thoai', 'Tong diem', 'Xep loai', 'Nhan xet'];
        const rows = reportData.map((st, idx) => [
            st.position,
            idx + 1,
            `"${st.name}"`, // Bọc trong ngoặc kép để tránh lỗi dấu phẩy trong tên
            st.group,
            st.plus,
            st.minus,
            st.phoneViolations,
            st.score,
            `"${st.rank.label}"`,
            `"${st.trendText}"`
        ]);
        
        // Thêm BOM (\uFEFF) để Excel nhận diện đúng font Unicode tiếng Việt
        const csvContent = "\uFEFF" + [headers.join(','), ...rows.map(e => e.join(','))].join('\n');
        const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
        const url = URL.createObjectURL(blob);
        const link = document.createElement("a");
        link.setAttribute("href", url);
        link.setAttribute("download", `Bang_Diem_Thi_Dua_${filterType === 'month' ? selectedMonth : 'Tuan'}.csv`);
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
    };

    return (
        <div>
            <div className="flex flex-col md:flex-row justify-between items-start md:items-center mb-6 gap-4">
                <h2 className="text-2xl font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-gray-800 to-gray-600">Bảng Tổng Kết Điểm Thi Đua</h2>
                <div className="flex flex-wrap items-center gap-3">
                    <div className="bg-gray-100/80 backdrop-blur-sm p-1.5 rounded-xl inline-flex shadow-inner">
                        <button 
                            onClick={() => setFilterType('week')}
                            className={`px-4 py-2 rounded-lg font-bold text-sm transition ${filterType === 'week' ? 'bg-white shadow-sm text-blue-700' : 'text-gray-500 hover:text-gray-700'}`}
                        >
                            7 ngày qua
                        </button>
                        <button 
                            onClick={() => setFilterType('month')}
                            className={`px-4 py-2 rounded-lg font-bold text-sm transition ${filterType === 'month' ? 'bg-white shadow-sm text-blue-700' : 'text-gray-500 hover:text-gray-700'}`}
                        >
                            Theo tháng
                        </button>
                    </div>

                    {filterType === 'month' && (
                        <div className="flex items-center bg-white border border-gray-200 rounded-xl px-3 py-1.5 shadow-sm">
                            <Calendar className="w-4 h-4 text-gray-400 mr-2" />
                            <select 
                                value={selectedMonth} 
                                onChange={e => setSelectedMonth(e.target.value)}
                                className="bg-transparent font-bold text-gray-700 outline-none cursor-pointer text-sm"
                            >
                                {availableMonths.map(m => (
                                    <option key={m} value={m}>Tháng {m.split('-')[1]}/{m.split('-')[0]}</option>
                                ))}
                            </select>
                        </div>
                    )}

                    <button 
                        onClick={handleExportExcel}
                        className="flex items-center gap-2 bg-emerald-500 hover:bg-emerald-600 text-white px-4 py-2 rounded-xl font-bold transition-all shadow-sm hover:shadow-md transform hover:-translate-y-0.5"
                    >
                        <Download className="w-4 h-4"/> Xuất Excel
                    </button>
                </div>
            </div>

            <div className="overflow-x-auto rounded-2xl border border-gray-100 shadow-lg bg-white">
                <table className="w-full text-left border-collapse min-w-[800px]">
                    <thead>
                        <tr className="bg-gradient-to-r from-slate-50 to-gray-50 border-b border-gray-200 text-sm text-gray-600 uppercase tracking-wider">
                            <th className="p-4 font-bold text-center w-12 text-blue-600">Hạng</th>
                            <th className="p-4 font-bold text-center w-12">STT</th>
                            <th className="p-4 font-bold">Họ và tên</th>
                            <th className="p-4 font-bold text-center">Tổ</th>
                            <th className="p-4 font-bold text-center text-emerald-600">Cộng</th>
                            <th className="p-4 font-bold text-center text-rose-600">Trừ</th>
                            <th className="p-4 font-bold text-center">Tổng điểm</th>
                            <th className="p-4 font-bold">Xếp loại</th>
                            <th className="p-4 font-bold">Nhận xét</th>
                        </tr>
                    </thead>
                    <tbody className="divide-y divide-gray-100">
                        {reportData.map((st, idx) => (
                            <tr key={st.id} className="hover:bg-blue-50/50 transition-colors duration-200 group">
                                <td className="p-4 text-center font-extrabold text-lg text-blue-600">
                                    {st.position === 1 ? '🥇' : st.position === 2 ? '🥈' : st.position === 3 ? '🥉' : st.position}
                                </td>
                                <td className="p-4 text-center text-gray-400 font-semibold group-hover:text-blue-500">{idx + 1}</td>
                                <td className="p-4 font-bold text-gray-800">
                                    {st.name}
                                    {st.title && <span className="ml-2 text-xs bg-gradient-to-r from-blue-100 to-indigo-100 text-blue-700 px-2 py-0.5 rounded-full font-bold shadow-sm">{st.title}</span>}
                                    {st.phoneViolations > 0 && (
                                        <span title="Vi phạm điện thoại" className="ml-2 inline-flex items-center text-xs text-rose-500 bg-rose-50 px-1.5 py-0.5 rounded-full font-semibold">
                                            <Smartphone className="w-3 h-3 mr-1"/> x{st.phoneViolations}
                                        </span>
                                    )}
                                </td>
                                <td className="p-4 text-center text-gray-600 font-medium">{st.group}</td>
                                <td className="p-4 text-center font-bold text-emerald-600 bg-emerald-50/30">{st.plus > 0 ? `+${st.plus}` : '-'}</td>
                                <td className="p-4 text-center font-bold text-rose-600 bg-rose-50/30">{st.minus > 0 ? `-${st.minus}` : '-'}</td>
                                <td className="p-4 text-center font-extrabold text-lg text-gray-800 bg-gray-50/50">{st.score}</td>
                                <td className="p-4">
                                    <span className={`px-3 py-1.5 rounded-full text-xs font-bold shadow-sm ${st.rank.bg} ${st.rank.color} border border-white/50`}>
                                        {st.rank.label}
                                    </span>
                                </td>
                                <td className="p-4">
                                    <div className={`flex items-center gap-1.5 text-sm font-bold ${st.trendColor}`}>
                                        {st.trendVal > 0 ? <TrendingUp className="w-4 h-4" /> : st.trendVal < 0 ? <TrendingDown className="w-4 h-4" /> : <Minus className="w-4 h-4" />}
                                        {st.trendText}
                                    </div>
                                </td>
                            </tr>
                        ))}
                    </tbody>
                </table>
            </div>
        </div>
    );
}

function HistoryView({ incidents, role, students }) {
    // If not Teacher, hide criteria 15 reporters to protect identity
    const visibleIncidents = [...incidents].reverse().filter(inc => {
        if (inc.criteriaId === 15 && role !== 'GVCN') return false; 
        return true;
    });

    return (
        <div>
            <h2 className="text-xl font-bold mb-4">Lịch sử ghi nhận</h2>
            <div className="space-y-3">
                {visibleIncidents.map(inc => {
                    const student = students.find(s => s.id === inc.studentId);
                    const isGroup = inc.criteriaId === 23;
                    const c = criteriaList.find(x => x.id === inc.criteriaId);
                    
                    return (
                        <div key={inc.id} className="p-3 border border-gray-100 rounded-lg flex items-center justify-between hover:bg-gray-50">
                            <div>
                                <div className="flex items-center gap-2">
                                    <span className="font-semibold">{isGroup ? `Tổ ${inc.groupId}` : student?.name}</span>
                                    <span className="text-xs text-gray-400">{inc.date}</span>
                                    {inc.status === 'confirmed' && <span className="text-xs bg-green-100 text-green-700 px-1.5 rounded font-bold">Đã duyệt</span>}
                                    {inc.status === 'pending' && <span className="text-xs bg-yellow-100 text-yellow-700 px-1.5 rounded font-bold">Chờ duyệt</span>}
                                    {inc.status === 'rejected' && <span className="text-xs bg-red-100 text-red-700 px-1.5 rounded font-bold">Từ chối</span>}
                                </div>
                                <div className="text-sm text-gray-600 truncate max-w-md">
                                    {c?.name} • Người ghi: {inc.reporterRole}
                                </div>
                            </div>
                            <div className={`font-bold ${c?.point > 0 ? 'text-green-600' : 'text-red-600'}`}>
                                {c?.point > 0 ? '+' : ''}{c?.point}
                            </div>
                        </div>
                    );
                })}
            </div>
        </div>
    );
}

function CriteriaView() {
    return (
        <div>
            <div className="mb-4">
                <h2 className="text-xl font-bold text-gray-800">Danh mục 30 Tiêu chí chính thức</h2>
                <p className="text-sm text-gray-500">Mỗi học sinh mặc định có 100 điểm/tuần. Mức điểm là cố định.</p>
            </div>
            
            <div className="space-y-6">
                {categories.map(cat => {
                    const crits = criteriaList.filter(c => c.categoryId === cat.id);
                    if(crits.length === 0) return null;
                    return (
                        <div key={cat.id} className="border border-gray-200 rounded-xl overflow-hidden">
                            <div className="bg-gray-50 px-4 py-2 font-bold text-gray-700 border-b border-gray-200">
                                {cat.id}. {cat.name}
                            </div>
                            <div className="divide-y divide-gray-100">
                                {crits.map((c, idx) => (
                                    <div key={c.id} className="flex justify-between items-center p-3 hover:bg-white bg-gray-50/30">
                                        <div className="text-sm text-gray-700 pr-4">
                                            <span className="font-medium mr-2">{c.id}.</span>
                                            {c.name}
                                        </div>
                                        <div className={`shrink-0 font-bold w-12 text-center rounded py-1 text-sm ${
                                            c.point > 0 ? 'bg-green-100 text-green-700' : 'bg-red-50 text-red-600'
                                        }`}>
                                            {c.point > 0 ? '+' : ''}{c.point}
                                        </div>
                                    </div>
                                ))}
                            </div>
                        </div>
                    );
                })}
            </div>
        </div>
    );
}

function RecordModal({ role, students, onClose, onSave }) {
    const [date, setDate] = useState(new Date().toISOString().split('T')[0]);
    const [criteriaId, setCriteriaId] = useState('');
    const [studentId, setStudentId] = useState('');
    const [groupId, setGroupId] = useState('');
    const [notes, setNotes] = useState('');
    const [reportedStudentId, setReportedStudentId] = useState(''); // For criteria 15

    const selectedCriteria = criteriaList.find(c => c.id === parseInt(criteriaId));
    const isGroupEvent = selectedCriteria?.isGroup;
    const isPhoneReport = selectedCriteria?.id === 15;

    const handleSubmit = (e) => {
        e.preventDefault();
        if (!criteriaId) return;
        if (isGroupEvent && !groupId) return;
        if (!isGroupEvent && !studentId) return;

        const newInc = {
            id: 'INC_' + Date.now(),
            criteriaId: parseInt(criteriaId),
            studentId: isGroupEvent ? null : studentId,
            groupId: isGroupEvent ? parseInt(groupId) : null,
            reportedStudentId: isPhoneReport ? reportedStudentId : null,
            point: selectedCriteria.point,
            reporterRole: role,
            reporterName: 'Người dùng', // in real app, get from auth
            date,
            status: 'pending',
            notes
        };

        onSave(newInc);
    };

    return (
        <div className="fixed inset-0 bg-slate-900/50 flex items-center justify-center p-4 z-50">
            <div className="bg-white rounded-2xl w-full max-w-lg shadow-2xl flex flex-col max-h-[90vh]">
                <div className="flex justify-between items-center p-5 border-b border-gray-100">
                    <h3 className="text-xl font-bold text-gray-800 flex items-center gap-2">
                        <PlusCircle className="text-blue-600"/> Ghi nhận vi phạm/tuyên dương
                    </h3>
                    <button onClick={onClose} className="text-gray-400 hover:text-gray-600">
                        <X className="w-6 h-6"/>
                    </button>
                </div>

                <div className="p-5 overflow-y-auto">
                    <form id="record-form" onSubmit={handleSubmit} className="space-y-4">
                        <div>
                            <label className="block text-sm font-medium text-gray-700 mb-1">Ngày ghi nhận</label>
                            <input 
                                type="date" required value={date} onChange={e => setDate(e.target.value)}
                                className="w-full border border-gray-300 rounded-lg p-2.5 focus:ring-2 focus:ring-blue-500 outline-none"
                            />
                        </div>

                        <div>
                            <label className="block text-sm font-medium text-gray-700 mb-1">Lỗi / Thành tích (30 Tiêu chí)</label>
                            <select 
                                required value={criteriaId} onChange={e => {
                                    setCriteriaId(e.target.value);
                                    setStudentId(''); setGroupId(''); setReportedStudentId('');
                                }}
                                className="w-full border border-gray-300 rounded-lg p-2.5 focus:ring-2 focus:ring-blue-500 outline-none"
                            >
                                <option value="">-- Chọn tiêu chí --</option>
                                {categories.map(cat => (
                                    <optgroup key={cat.id} label={`${cat.id}. ${cat.name}`}>
                                        {criteriaList.filter(c => c.categoryId === cat.id).map(c => (
                                            <option key={c.id} value={c.id}>
                                                {c.id}. {c.name} ({c.point > 0 ? '+' : ''}{c.point})
                                            </option>
                                        ))}
                                    </optgroup>
                                ))}
                            </select>
                        </div>

                        {selectedCriteria && (
                            <div className={`p-3 rounded-lg flex items-center gap-2 text-sm font-bold border ${selectedCriteria.point > 0 ? 'bg-green-50 text-green-700 border-green-200' : 'bg-red-50 text-red-700 border-red-200'}`}>
                                Điểm tự động: {selectedCriteria.point > 0 ? '+' : ''}{selectedCriteria.point} điểm
                            </div>
                        )}

                        {isGroupEvent ? (
                            <div>
                                <label className="block text-sm font-medium text-gray-700 mb-1">Chọn Tổ vi phạm</label>
                                <select 
                                    required value={groupId} onChange={e => setGroupId(e.target.value)}
                                    className="w-full border border-gray-300 rounded-lg p-2.5 focus:ring-2 focus:ring-blue-500 outline-none"
                                >
                                    <option value="">-- Chọn tổ --</option>
                                    <option value="1">Tổ 1</option>
                                    <option value="2">Tổ 2</option>
                                    <option value="3">Tổ 3</option>
                                    <option value="4">Tổ 4</option>
                                </select>
                            </div>
                        ) : (
                            <div>
                                <label className="block text-sm font-medium text-gray-700 mb-1">
                                    {isPhoneReport ? 'Người phát hiện & Báo cáo (Bảo mật)' : 'Học sinh'}
                                </label>
                                <select 
                                    required value={studentId} onChange={e => setStudentId(e.target.value)}
                                    className="w-full border border-gray-300 rounded-lg p-2.5 focus:ring-2 focus:ring-blue-500 outline-none"
                                >
                                    <option value="">-- Chọn học sinh --</option>
                                    {students.map(s => (
                                        <option key={s.id} value={s.id}>{s.name} (Tổ {s.group}) {s.title ? `- ${s.title}` : ''}</option>
                                    ))}
                                </select>
                            </div>
                        )}

                        {isPhoneReport && (
                            <div className="bg-blue-50 p-4 rounded-lg border border-blue-100">
                                <label className="block text-sm font-medium text-blue-800 mb-1 flex items-center gap-1">
                                    <Smartphone className="w-4 h-4"/> Học sinh mang điện thoại (Để GVCN xác minh)
                                </label>
                                <select 
                                    required value={reportedStudentId} onChange={e => setReportedStudentId(e.target.value)}
                                    className="w-full border border-blue-200 rounded-lg p-2.5 outline-none mb-2"
                                >
                                    <option value="">-- Chọn bạn vi phạm --</option>
                                    {students.filter(s => s.id !== studentId).map(s => (
                                        <option key={s.id} value={s.id}>{s.name}</option>
                                    ))}
                                </select>
                                <p className="text-xs text-blue-600">
                                    * Chỉ cộng điểm khi GVCN đã xác minh sự thật. Danh tính người báo cáo được giữ kín.
                                </p>
                            </div>
                        )}

                        <div>
                            <label className="block text-sm font-medium text-gray-700 mb-1">Nội dung chi tiết / Minh chứng</label>
                            <textarea 
                                value={notes} onChange={e => setNotes(e.target.value)}
                                rows={3} placeholder="Mô tả sự việc hoặc ghi chú minh chứng..."
                                className="w-full border border-gray-300 rounded-lg p-2.5 focus:ring-2 focus:ring-blue-500 outline-none resize-none"
                            ></textarea>
                        </div>
                    </form>
                </div>
                
                <div className="p-4 border-t border-gray-100 bg-gray-50 rounded-b-2xl flex justify-end gap-3">
                    <button type="button" onClick={onClose} className="px-5 py-2 text-gray-600 font-medium hover:bg-gray-200 rounded-lg transition">
                        Hủy
                    </button>
                    <button type="submit" form="record-form" className="px-5 py-2 bg-blue-600 text-white font-bold rounded-lg hover:bg-blue-700 transition">
                        Gửi duyệt
                    </button>
                </div>
            </div>
        </div>
    );
}

function ClassManageView({ students, setStudents }) {
    const handleGroupChange = (id, newGroup) => {
        setStudents(students.map(s => s.id === id ? { ...s, group: parseInt(newGroup) || '' } : s));
    };
    const handleTitleChange = (id, newTitle) => {
        setStudents(students.map(s => s.id === id ? { ...s, title: newTitle } : s));
    };

    return (
        <div>
            <h2 className="text-xl font-bold mb-4 flex items-center gap-2">
                <Users className="text-blue-600" /> Quản lý Tổ & Phân công nhiệm vụ
            </h2>
            <p className="text-sm text-gray-500 mb-4">
                Giáo viên có thể cập nhật lại Tổ (khi học sinh đổi chỗ) và nhập chức vụ (Tổ trưởng, Lớp trưởng, Sao đỏ...). Chức vụ sẽ được tự động hiển thị cạnh tên học sinh trong các bảng báo cáo và danh sách chọn.
            </p>
            
            <div className="overflow-x-auto rounded-xl border border-gray-200 shadow-sm">
                <table className="w-full text-left border-collapse bg-white">
                    <thead>
                        <tr className="bg-gray-50 border-b border-gray-200 text-sm text-gray-600">
                            <th className="p-3 font-semibold text-center w-12">STT</th>
                            <th className="p-3 font-semibold">Họ và tên</th>
                            <th className="p-3 font-semibold text-center w-24">Tổ</th>
                            <th className="p-3 font-semibold">Chức vụ / Nhiệm vụ</th>
                        </tr>
                    </thead>
                    <tbody className="divide-y divide-gray-100">
                        {students.map((st, idx) => (
                            <tr key={st.id} className="hover:bg-gray-50 transition">
                                <td className="p-3 text-center text-gray-500 font-medium">{idx + 1}</td>
                                <td className="p-3 font-medium text-gray-800">{st.name}</td>
                                <td className="p-3 text-center">
                                    <input 
                                        type="number" 
                                        min="1" max="10"
                                        value={st.group || ''}
                                        onChange={(e) => handleGroupChange(st.id, e.target.value)}
                                        className="w-16 border border-gray-300 rounded p-1.5 text-center outline-none focus:ring-2 focus:ring-blue-500 text-sm"
                                    />
                                </td>
                                <td className="p-3">
                                    <input 
                                        type="text" 
                                        placeholder="VD: Lớp trưởng, Tổ trưởng..."
                                        value={st.title || ''}
                                        onChange={(e) => handleTitleChange(st.id, e.target.value)}
                                        className="w-full max-w-xs border border-gray-300 rounded p-1.5 outline-none focus:ring-2 focus:ring-blue-500 text-sm"
                                    />
                                </td>
                            </tr>
                        ))}
                    </tbody>
                </table>
            </div>
        </div>
    );
}
