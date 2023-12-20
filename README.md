
@Repository
public interface EstudianteRepo extends JpaRepository<Estudiante, String> {
    @Query("SELECT e FROM estudiante e WHERE e.cedula = :ced")
    Estudiante findByCedula(@Param("ced") String ced);

    @Query("SELECT e FROM estudiante e WHERE e.cedula=:palabra")
    List<Estudiante> findAll(String palabra);

}
Servicio
 @Autowired
    private EstudianteRepo estudianteRepo; // Intectar informacion a nuestro servicio
 public List<Estudiante> mostrar(String buscar) {
        if (buscar != null) {
            return estudianteRepo.findAll(buscar);

        }
        return estudianteRepo.findAll();
    }

    public Estudiante insertar(Estudiante estudiante) {
        return estudianteRepo.save(estudiante);
    }

    public Estudiante actualizar(Estudiante estudiante) {
        return estudianteRepo.save(estudiante);
    }

    public Estudiante buscarId(String id) {
        return estudianteRepo.findByCedula(id);
    }

    public void eliminar(Estudiante estudiante) {
        estudianteRepo.delete(estudiante);
    }
    entity
    @Entity
@Data
@Table(name = "ESTUDIANTES")
public class Estudiante implements Serializable {
    @Id
    private String cedula;
    private String nombre;
    private String apellido;
    private String direccion;
    private String telefono;
